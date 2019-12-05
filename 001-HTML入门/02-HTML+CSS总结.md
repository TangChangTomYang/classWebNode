## HTML元素

- 脱标元素
  - 特点
    - 可以随意设置宽高
    - 如果没有设置宽高，宽高由内容决定
    - 不再受标准流（normal flow）的约束
      - 不再严格区分块级元素、行内级元素
    - 元素内部默认还是按照标准流
  - 哪些元素是脱标元素
    - 浮动元素
      - float:left
      - float:right
      - 浮动元素之间不能层叠
      - 浮动元素不能跟行内级内容层叠
    - 绝对定位元素
      - position:absolute
      - position:fixed
      - 通过z-index可以设置元素的层叠顺序
- 非脱标元素
  - 块级元素（基本都是非替换）
    - div、p、pre、table、form、h1~h6
    - ul、li、ol、dl、dt、dd
    - header、footer、nav、section、article、aside
    - 独占一行
    - 可以随意设置宽高
    - 如果不设置高度，高度默认由内容决定
  - 行内级元素
    - 替换元素
      - img、input、iframe、canvas、object
      - video、audio
      - 可以跟其他行内级元素在同一行显示
      - 可以随意设置宽高
    - 非替换元素
      - span、strong、a、em、i
      - 可以跟其他行内级元素在同一行显示
      - 不可以随意设置宽高
      - 如果不设置宽高，宽高默认由内容决定
  - inline-block
    - 可以跟其他行内级元素在同一行显示
    - 可以随意设置宽高
    - 如果不设置宽高，宽高默认由内容决定



## CSS属性

- 盒子模型

  - width、min-width、max-width
  - height、min-height、max-height
  - padding、padding-top、padding-right、padding-bottom、padding-left
  - margin、margin-top、margin-right、margin-bottom、margin-left
  - border、border-top、border-right、border-bottom、border-left
    - 可以利用边框生成三角形
  - box-sizing
    - content-box
      - width不包括padding和border，height不包括padding和border
    - border-box
      - width = padding + border + 内容宽度
      - height = padding + border + 内容高度
  - box-shadow
    - box-shadow: 2px 5px 10px 7px rgba(0,0,0,.2) inset
      - 2px：向右偏移2px
      - 5px：向下偏移5px
      - 10px：模糊半径（模糊度，这个值越大，越模糊）
      - 7px：扩散半径（值越大，扩散范围月光）
      - inset：阴影显示到元素内部（如果不加inset，看显示在元素外部）
  - overflow
    - visible：溢出内容仍然可见
    - hidden：溢出内容直接隐藏
    - scroll：会一直显示水平、垂直方向的滚动条
    - auto：会自动根据内容的溢出情况来决定是否显示滚动条
  - 对于行内级非替换元素（span、strong、a等）
    - margin-top、margin-bottom不起作用
    - padding-top、padding-bottom、border-top、border-bottom的效果比较特殊
  - 对于块级元素（比如div、p等）
    - 存在margin-top、margin-bottom传递的问题（传递给块级父元素）
    - 存在margin-top、margin-bottom折叠问题（margin collapse）
    - 包含块的宽度 = margin-left + margin-right + 块级元素实际占用的宽度

- 定位

  - position
    - static
      - 默认（非定位元素）
      - 不脱离标准流
      - 不能通过left、right、top、bottom调整位置
    - relative
      - 相对定位（定位元素）
      - 不脱离标准流
      - 可以通过left、right、top、bottom调整位置
      - 定位参照对象是自己原来的位置
    - absolute
      - 绝对定位（定位元素，绝对定位元素）
      - 脱离标准流
      - 可以通过left、right、top、bottom调整位置
      - 定位参照对象
        - 最邻近的定位祖先元素（从祖先元素中找到最邻近的定位元素）
        - 如果找不到这样的祖先元素，那么就参照视口（viewport）
      - 很多情况下，子元素都会参照父元素进行绝对定位，常用做法是：子绝父相
        - 子元素：position: absolute
        - 父元素：position: relative
    - fixed
      - 固定定位（定位元素，绝对定位元素）
      - 脱离标准流
      - 可以通过left、right、top、bottom调整位置
      - 定位参照对象
        - 视口（viewport）
    - 对于绝对定位元素来说
      - 包含块的宽度 = left + right + margin-left + margin-right + 元素的实际占用宽度
      - 包含块的高度 = top + bottom + margin-top + margin-bottom + 元素的实际占用高度
    - 对于定位元素来说
      - 有时候会利用left、margin-left联合使用来让一个元素水平居中
        - left: 自己宽度的一半乘以负一
        - margin-left: 50%

- 文字

  - color：前景色（文字颜色、边框颜色、文字装饰线颜色，#fff、#ffffff、rgb(255,255,255)、rgba(255,255,255,.5)）

  - text-align

    - 设置元素的内容在元素中的水平位置
    - left：左对齐
    - right：右对齐
    - center：居中

  - text-indent

    - 一般用来设置首行文本的缩进
    - 常见用法
      - text-indent: 2em
      - 刚好缩进2个文字

  - text-decoration

    - 设置文字装饰线
    - underline：下划线
    - line-through：删除线（比如电商网站的原价）
    - none：去除删除线

  - text-overflow

    - 设置隐藏掉的溢出文字内容的表现形式

    - clip：溢出的内容直接裁剪

    - ellipsis：溢出的内容用省略号显示

    - 让一个元素永远只显示一行文字，并且溢出部分显示省略号

    - ```
      white-space: nowrap; /* 永远只显示一行文字 */
      overflow: hidden; /* 隐藏溢出的内容 */
      text-overflow: ellipsis; /* 隐藏掉的内容用省略号来表示 */
      ```

- 字体

  - font-family：字体名称
    - 可以设置多个字体名称，它们之间用逗号隔开
    - 一般英文字体写在前面，中文字体写在后面
  - font-weight：设置轻重（粗细）
    - 100~900
    - bold：700
    - normal：400
  - font-size：设置字体大小
    - font-size: 10px
    - font-size: 10%
      - 使用父元素的font-size乘以10%
      - 继承父元素的font-size时，继承的是计算值，不是直接继承10%
    - font-size: 0.5em
      - 使用父元素的font-size乘以50%
    - width: 2em
      - 使用自己的font-size乘以2
  - line-height
    - line-height: 20px
    - line-height: 20%
      - 使用自己的font-size乘以20%
    - line-height: 2em
      - 使用自己的font-size乘以2
    - line-height: 2
      - 使用自己的font-size乘以2
    - 如果希望一行文字垂直居中，常见做法是
      - 设置line-height和height保持一致
  - font-style
    - normal：正常
    - italic：斜体
    - oblique：倾斜
  - font
    - 简写属性
    - font-size/line-height  font-family

- 背景

  - background-color：背景色
  - background-image：背景图片
  - background-repeat
    - repeat
    - repeat-x
    - repeat-y
    - no-repeat
  - background-position
    - background-position: 10px 20px
    - background-position: right top;
    - background-position: center top;
  - background-size：设置背景图片的大小
  - background：简写属性
    - background: url("1.png") no-repeat left top/20px 20px #f00;
  - CSS Sprite
    - 精灵图片
    - 雪碧图片

- 动画

  - transition

    - 用于决定哪些CSS属性需要参与动画
    - transition: all 2s;
      - 所有可动画CSS属性的修改，都会在2s的时间内通过动画完成

  - transform

    - 平移
      - translateX(10px)
      - translateY(30px)
      - translate(10px, 30px)
    - 缩放
      - scaleX(0.5)
      - scaleY(0.5)
      - scale(0.5)
    - 旋转
      - rotate(45deg)：二维平面旋转
      - rotateX(45deg)：绕着x轴旋转
      - rotateZ(45deg)：绕着Z轴旋转（跟rotate()类似）
      - rotateY(45deg)：绕着Y轴旋转
    - transform: translate(20px, 30px)  scale(0.5)  rotate(45deg);

  - animation

    - 使用步骤

      - 创建动画

      - ```
        @keyframes my-anim1 {
            from {
                
            }   
            
            to {

             }
        }

        @keyframes my-anim2 {
            0% {

            }

            20% {

            }

            60% {

            }

            100% {

            }
        }
        ```

      - 使用动画

        - animation-duration：动画的持续时间
        - animation-name：动画名称
        - animation-iteration-count：动画执行次数
          - infinite：代表无限次数执行
        - animation-timing-function：动画的执行节奏
        - animation：简写属性
          - animation: my-anim 2s infinite

  - 3D透视

    - ```
      /* 给父元素增加 */
      transform-style: preserve-3d;
      perspective: 500px;
      ```