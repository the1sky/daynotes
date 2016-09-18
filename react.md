####react笔记


#####[react-lazy-load](https://github.com/loktar00/react-lazy-load)


要点:

######父级容器计算规则

    overfolow=scroll || auto

######判断元素是否在父级容器

    #1 父级容器区域:

    top,left,offsetWidth,offsetHeight

    #2 判断:

    if (typeof container === 'undefined' || container === window) {
        top = window.pageYOffset;
        left = window.pageXOffset;
        bottom = top + window.innerHeight;
        right = left + window.innerWidth;
      } else {
        const containerOffset = offset(container);

        top = containerOffset.top;
        left = containerOffset.left;
        bottom = top + container.offsetHeight;
        right = left + container.offsetWidth;
      }

######兼容background-image

######需要配置offset及height

    我一般设置offsetVertical


#####onlyActiveOnIndex

    <Link onlyActiveOnIndex activeStyle={{color:'#53acff'}} to='/'>Home</Link>



