####node,express相关问题记录


#####winston日志级别及输出

######默认级别

    { error: 0, warn: 1, info: 2, verbose: 3, debug: 4, silly: 5 }

    高  ->  低

######一个实例多个transport的输出规则

#######示例

    var logger = new (winston.Logger)({
        transports: [
          new (winston.transports.File)({
            filename: 'info.log',
            level: 'info'
          }),
          new (winston.transports.File)({
            filename: 'debug.log',
            level: 'debug'
          }),
          new (winston.transports.File)({
            filename: 'error.log',
            level: 'error'
          }),
        ]
      });
#######规则

    #1  低级别包含高级别的输出
    #2  如上:

        error只包含error
        info包含error
        debug包含info,error

######比较实用的日志输出解决方案

> 很明显上述输出将会有大量的数据冗余

> 利用多实例方案


######示例代码

#######logger.js模块

    var winston = require('winston');

    /**
     * 正常的日志处理器
     */
    var logger = new winston.Logger({
      transports: [
        new (winston.transports.File)({
          level: 'info',
          filename: 'access.log',
        })
      ],
      exitOnError: false
    });

    /**
     * error日志处理器
     */
    var errorLogger = new winston.Logger({
      transports: [
        new (winston.transports.File)({
          level: 'error',
          filename: 'error.log',
        })
      ],
      exitOnError:false
    });

    /**
     * debug日志处理器
     */
    var debugLogger = new winston.Logger({
      transports: [
        new (winston.transports.File)({
          level: 'debug',
          filename: 'debug.log',
        })
      ],
      exitOnError: false
    });

    module.exports = {
      info:logger.info,
      debug:debugLogger.debug,
      error:errorLogger.error
    };
    module.exports.stream = {
      write: function (message, encoding) {
        logger.info(message.slice(0, -1));
      }
    };

#######使用

    #1  作为express的日志输出

        app.use(require('morgan')('combined',{"stream": logger.stream}));

    #2  使用

        var logger = require('logger');
        logger.info('info');
        logger.error('error');
        logger.debug('debug');


#####阳光明媚,为什么不出去走走
