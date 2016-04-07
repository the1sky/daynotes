####near-fs全栈开发框架


#####目标

    #   一切皆组件
    #   方便进行react/angular切换
    #   server-rendering
    #   不重复编译
    #   支持es6,es7,ts
    #   socket支持

#####待解决问题

    #   文件的md5戳,无变化时不处理
    #   server rendering前的数据处理逻辑
    #   高性能log系统,目前想查找问题比较弱
    #   缺少数据库处理模块
    #   高可配置,基于目前的gulpfile改进
    #   根据路由分别编译处理,可以考虑引入webpack
    #   react组件的内联css问题, 高内聚,可重用
        参考这个:https://github.com/FormidableLabs/radium#how-does-radium-work
    #   怎么样方便的集成第三方模块?(利用express的中间件?)

####目录结构

    --app                               #前端展示主体,组件化
        --react
            --actions
            --components
            --stores
            --routes
            --alt.js

        --angular
            --components
            --routes
    --api                               #系统调用第三方API
        --base.js
    --db                                #系统调用第三方数据库
        --base.js                       #支持mongo,mysql,postgresql,sqlite
    --browser                           #供浏览器使用资源
        --scss
        --js
            --lib
        --imgs
        --fonts
        --sound
        --templates

    --config

    --routes                            #系统对外的路由,包括api服务等

    --server
        --server.js
        --render.js
        --logger.js
        --connect
            --before-render.js

    --public                            #browser的编译目标目录
        browser中的除templates外的任何内容

    --views                             #browser中的templates的编译目标目录
        broser中的templates编译后的结果

    --gulp | webpack                    #工程化工具
        各种gulp配置

        --gulp all:prod
        --gulp all:dev
        --gulp entry-name:prod
        --gulp entry-name:dev

    --doc
        文档
    --test
        测试
