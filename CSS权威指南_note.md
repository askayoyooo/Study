#第二章 选择器
##    1.基本规则_规则结构
        选择器 + 声明块（一个或多个声明（属性+值(一个关键字或者该属性可取关键字的一个列表（由空格隔开）)））
        h1 {color:red; background:yellow;}
        p {font: medium Helvetica;}
        p {font: large/150% sans-serif;}/* 只有这种情况下使用（/）来分隔两个特定的关键则*/
##    2.选择器种类
        元素选择器，类选择器，ID选择器，属性选择器，后代选择器，伪类选择器，伪元素选择器
        
####        1.元素选择器
            文档的元素，为最基本的选择器，例如：
            html {color:black;}
            h1 {color:gray;}
            h2 {color:silver;}
####        2.选择器分组
            将选择器放在规则的左边，使用逗号分隔。
            h1, p {color:gray;}
####        3.通配选择器
            * {color: red;}/*可以让每一个元素都为红色*/
####        4.声明分组
            h1 {font: 18px Helvetica; color: purple; background: aqua;}/*注意每个声明后面必须跟（；）*/
####        5.结合选择器分组和声明分组
            h1, h2, h3, h4, h5, h6,{color: gray; 
                                    background: white; 
                                    padding: 0.5em; 
                                    border: 1px solid black; 
                                    font-family: Charcoal, sans-serif;}
####       6.类选择器和ID选择器
            需要适当地标记文档后才能使用这些选择器。
####        7.类选择器
            .+选择器名
            元素需添加class 属性，例如：
            <p class=“warning”>This is a warning paragraph</p>
            *.warning {font-weight: bold;}
            p.warning {font-weight: bold;}
####        8.多类选择器
            一个元素可以有多个类中间用空格表示,并且不分顺序。
            <p class="warning urgent">This is a urgent warning paragraph</p>
            .warning.urgent {background: silver} /*同时属于warning和urgent类的元素背景被设置为silver，假如有三个类，
            但是这三个类包好了warning，urgent,那么这个元素也会被设置为silver*/
            !   IE7以前的版本只会识别多类选择器中的最后一个类。
####        9.ID选择器
            #+选择器名
            元素需添加id属性，例如：
            <p id="lead-para">This paragraph will be boldfaced.</p>
            <p>This paragraph will not be bold.</p>
            *#lead-para {font-weight:bold;}/*如果多个元素ID被错误地设为相同，则所有元素都会被应用此ID对应的规则*/
####        10.类选择器还是ID选择器
            ID选择器不能结合使用，ID属性不允许有以空格分隔的词列表。
            .+类名的记法不支持XML,而#+ID的记法支持任何文档语言。
            类选择器和ID选择器可能是区分大小写的，这取决于文档语言。HTML和XHTML将类和ID值定义为区分大小写。
####        11.属性选择器
            类选择器和ID选择器实际上只是选择属性值。
            属性选择器根据元素的属性和属性值来选择元素。
            h1[class] {color:silver;}/*所有被设置class属性的h1都会被选择设置为silver*/
            img[alt] {border: 3px solid red;}/*对所有设置了alt的图像应用该规则，多用于诊断图像是否有效*/
            *[title] {font-weight: bold;}/*所有包含title的元素显示为粗体*/
            a[href][title] {font-weight: bold;}/*对于所有有href和title的超链接设置为粗体*/
            根据具体的属性选择
            a[href="http://www.example.com"] {font-weight: bold;}/*对特定属性应用规则*/
            a[href="http://www.example.com"][title="test"] {font-weight: bold;}/*对多条特定属性应用规则*/
            ! 此方法如果遇到class属性中有多个值由空格分隔，则容易出现问题。
            根据部分属性值选择
            <p class="warning urgent">This is a test</p>
            p[class~="warning"] {font-weight:bold;}/*必须注意class后面的~~~~~~~~~~~~如果没有~则需要属性值完全匹配*/
            p[class~="warning"] 与p.warning 是等价的。
            但是~=不仅可以应用于class,还可以应用于title=“ This is a tile”中p[title~="is"]就可以匹配该元素。
####       12.子串匹配属性选择器
            [foo^="bar"]选择foo属性值以bar开头的所有元素
            [foo$="bar"]选择foo属性值以bar结尾的所有元素
            [foo*="bar"]选择foo属性值中包含子串bar的所有元素
####       13.特定属性选择类型
            *[lang|="en"] {color: white;}/*lang属性以en开头的所有元素*/
            此种属性选择器最常用的是匹配语言值。            
##    3.使用文档结构
####         1.理解父子关系
                出现在某元素上层的元素为父元素，出现在下层的为子元素
####         2.后代选择器（又称为包含选择器）
                h1 em {color: gray;}/*注意没有逗号*/
                可能被忽略的一点是，em是h1的后代，但不管中间隔多少层。
####         3.选择子元素
                如果只想选择子元素，而不是后代元素则可以使用
                h1 > strong {color: red;}/*只会选择h1第一层的strong元素，而其余后代元素即使是strong元素*/
####         4.选择相邻兄弟元素
                如果要去除h1元素后面的段落的上边距：
                 h1 + p {margin-top: 0;}/*h1与p要有相同的父元素*/
##     4.伪类和伪元素
                利用此类选择器可以为文档中不一定存在的结构指定样式，或者为某些元素的状态所指示的幻想类指定样式
####         1.伪类选择器
                锚元素a,会有访问过和未访问过的两种锚类型，这些类型称为伪类，使用这些伪类的选择器则称为伪类选择器
                CSS定义类伪类，让访问过的锚有一个visited 类。则：
                a:visited {color: red;}/*注意visited前面的（：）其中这个用来分隔a和visited的冒号是伪类或伪元素的名片*/
####         2.链接伪类
                超链接是有href属性的所有a元素。
                ：link  指示作为超链接并指向一个未访问过的地址的所有锚。
                ：visited  指示作为已访问地址超链接的所有锚。
                a:link {color： blue;}
                a:visited {color: red;}
                以上两句等价于<body link="blue" vlink="red">
                a.external:link, a.external：visited {color: red;}/*为class属性为external的锚通过伪类指定规则*/
####         3.动态伪类
                根据用户的行为改变文档的外观。这些伪类总用来设置超链接的样式。
                 :focus 指当前拥有输入焦点的元素（可以接受键盘输入或者能以某种方式激活的元素）
                 :hover 指鼠标指针停留在哪个元素上。
                 :active 指示被用户输入激活的元素。
                 伪类的顺序很重要通常：link-visited-focus-hover-active
                 动态伪类可以应用到任何元素。
####          4.选择第一个子元素
                  静态伪类 ：first-child
                  p:first-child {color: red;}
                  其选择的是作为第一个子元素的P元素，而不是P元素的第一个子元素。
####          5.根据语言选择
                  ：lang()伪类可以根据元素的语言来选择。
                  *：lang(fr) {front-style: italic;}/*将所有法语元素变成斜体*/
                  需要语言特定演示的时候，大多数情况下伪类是更好的选择。
####          6.结合伪类
                  a:link:hover:lang(de) {color: red;}/*将德语语言的未访问链接鼠标放上时显示红色*/
                  a:visited:hover:lang(de) {color: silver;}/*将德语语言的已访问链接鼠标放上是显示红色*/
##      5.伪元素选择器
                就像伪类为锚点指定幻象类一样，伪元素能够在文档中插入假想的元素，从而达到某种效果
####          1.设置首字母样式
                  p:first-letter {color: red;}/*将每一段的第一个字母变成红色*/
                  h2:first-letter {font-size: 200%;}/*h2的第一个字母大小是标题字母大小的两倍*/
                  这种为元素并不直接出现在源代码中，而是由用户代理动态构造的。
####          2.设置第一行的样式
                  p:first-line {color: purple;}/*每一段的第一行会变成紫色*/
####          3.：first-letter 和first-line的限制
                  在CSS2中此伪元素只能用于标记或段落之类的块级元素，而不能用于超链接等行内元素。
                  属性限制见CSS权威指南第三版page66
                  所有伪元素都应该放在出现该伪元素的选择器最后面。
####          4.设置之前和之后元素的样式
                  h2:before {content:"[]"; color: silver;}/*在每个h2元素前加一堆银色中括号*/
                  伪元素用于插入生成的内容并为其设置样式。
                  body:after {content: "The End.".}
#第三章 结构与层叠
    每个合法文档都会生成一个结构树，这也是CSS继承的核心。继承是从一个元素向其后代元素传递属性值所采用的机制。本章将讨论
    特殊性、继承和层叠
##      1.特殊性
            特殊性值表述为4各部分，如0,0,0,0
            选择器中给定的各个ID属性值，加0,1,0,0
            选择器中给定的各个类属性值，属性选择或伪类，加0,0,1,0
            选择器中给定各个元素和伪元素，加0,0,0,1
            结合符和通配选择器对特殊性没有任何贡献
####           1.声明和特殊性
                   用户代理会解组成单独的规则，分组选择器也会被分解开。如：
                   h1, h2.section{color: silver; background: black;}
                   用户代理将其处理为
                   h1 {color: silver;}/*0001*/
                   h1 {background: black;}/*0001*/
                   h2.section {color: silver;}/*0011*/
                   h2.section {background: silver;}/*0011*/
####           2.通配选择器特殊性
                   通配选择器对一个选择器的特殊性没有贡献。即：0000
####           3.ID和属性选择器的特殊性
                   ID选择器和指定id属性的选择器在特殊性上有所不同。
                   tr[id="name"] td ul >li {color: maroon;}/*0017*/
                   li#answer {color: red;}/*0101*/
                   ID选择器胜出。
####           4.内联样式特殊性
                   一般的第一个0是为内联样式声明所保留的。它比其他声明的特殊性都高。
####           5.重要性
                   有时候某个声明非常重要，就在这些声明结束分号之前插入！important标志。
                   p.dark {color: #333 !important; background: white;}
#####                   所有重要声明标志的声明都分组在一起，重要声明的冲突会在重要声明内部解决。
#####                    如果一个重要声明和非重要声明冲突，则重要声明胜出。
##        2.继承
                样式不仅应用到指定的元素，还会应用到它的后代元素。
                继承对无序列表也适用。
                有些属性不能继承
                    属性border用来设置边框不能被继承。
                继承的值没有特殊性，连0特殊性都没有。0特殊性比无强！
                通配选择器的特殊性0高于继承的特殊性无。
                #toolbar {color: white; background: black;}
                如果Toolbar中有a连接，以上规则有可能达不到想要的效果，如果要避免则：
                #toolbar a:link {color:white;}
##        3.层叠
                如果特殊性相同，则按照出现顺序对应到给定元素的所有声明排序，一个声明在文档中越后出现它的权重就越大。
#####           如果有出现导入的样式表，则导入的排在前面，即导入的样式表权重小。
####            1.按权重和来源排序
                    ！important 胜出与style属性，
                    元素与创作样式表正常权重匹配，又与读者样式表中的正常权重匹配，则会使用创作人员样式。
#####                如果创作样式表和读者样式表都有!important标志，则读者样式表胜出。
                    在声明权重的方面考虑5级：
                    1.读者重要声明
                    2.创作人员的重要声明
                    3.创作人员的正常声明
                    4.读者的正常声明
                    5.用户代理的正常声明
####            2.按特殊性排序
                    一个元素的多个彼此冲突的声明，如果权重相同，则按照特殊性排序
####            3.按照顺序排序
                    如果两个规则的权重，来源和特殊性都完全相同，那么在样式表中后出现的一个胜出。
                    style属性放在其他规则的后面。
                    连接样式顺序(LVHA)：
                    :link{color: blue;}
                    :visited {color: purple;}
                    :hover {color: red;}
                    :active {color: orange;} 
####            4.非CSS表现提示
                    文档可能包含非css表现提示。如<font></font>元素,此类非CSS表现提示被处理为特殊性为0，并出现在创作
                    人员的样式表最前面。只要有创作人员或者读者样式，这种表现就会被覆盖，但是用户代理样式不能将其覆盖。
#第四章 值和单位
##    数字
            CSS中有整数和实数，这两种都是合法的，但是属性会限制所允许的数字范围。
##    百分数
            百分数一般是相对的，这个相对的值可能是同艺元素的另一个属性，也可以是从父级元素继承的一个值，或者祖先元素的一
            个值。接受百分数的值定义某些限制，还会定义百分数计算到什么程度。
##    颜色
            有两种不同的选择，一种是选择几种为数不多的颜色，如red,blue etc.
            或者一种不那么一目了然的方法，十六进制代码。
####        命名颜色
                aqua 浅绿色#0FF        fuchsia 浅莲红#F0F     lime 绿黄色#0F0        olive 橄榄色#808000       
                red 红色#F00      white 白色#FFF             black 黑色#000        gray 灰色#808080        
                maroon 栗色#800000       orange 橙色#F60       silver 银色         yellow 黄色#FF0
                blue 蓝色#00F     green 绿色#008000        navy 深蓝色#000080        purple 紫色#800080
                teal 青色#008080
####        用RGB指定颜色
####        函数式RGB颜色                
                  一般语法rgb(color)
                  百分数法：白色rgb(100%,100%,100%) 黑色rgb(0%,0%,0%)
                  三元整数法：rgb(255,255,255),
####        十六进制RGB颜色
                h1 {color: #FF0000;}/*set h1s to red*/
                h2 {color:#RRGGBB;}
                H3 {color: #FFF;}/*浏览器会取每一位将其复制为两位*/
####        颜色汇总
                参照命名颜色
####        Web安全颜色
                256色计算机上总能避免抖动的颜色。Web安全颜色可以表示为RGB值20%和51（十六进制为33）的背时。
                0%和0也是安全值。
                十六进制是（0,3,6,9,C,F）
##   长度单位
            长度单位可以划归为两类：绝对长度单位和相对长度单位。
####        绝对长度单位
                    in(英寸)  1in=2.54cm=254mm
                    cm(厘米)
                    mm(毫米)  
                    pt(点)    1in=72pt
                    pc(派卡)  1pc=12pt
####        处理绝对长度
                    在浏览器显示方面，em,百分数，甚至像素都比点要好。
                    在Web设计中使用绝对长度往往不是最佳的做法。以下相对长度单位
####        相对长度单位
                    他是根据与其他事物的关系度量的。某些相对单位，其大小几乎总是对应使用该单位的元素，因此会因元素的不同
                    而不同。
                    共有3中相对长度单位em,ex 和px.
                    em: em-height
                    ex: x-height
                    以上为两种常用的印刷度量单位。
                    px:像素，显示器上个一个个小点，之所以被定义为相对长度单位，是因为不同的显示器其单位长度的像素密度
                    不同。
####        em和ex单位
                    1个em定义为一种给定字体的font-size值。如果一个元素的font-size为14像素，那么对于该元素，1em就等于14
                    像素。
                    em的值会相对于父元素的字体大小改变。
                    ex是指所用字体中小写x的高度。
####        像素长度
                    如果使用响度设置字体大小，那么IE7之前的用户无法用浏览器文本大小调整字体大小。
                    非常适合用像素度量图像的大小。
####        像素理论
                    像素被定义为相对度量单位 page96
####        如何取舍
                    最好的度量单位可能是em,如果合适也可以使用px.
                    对于元素的边框和定位可能更加适合使用像素。
##      URL
               一般格式： url(protocol://server/pathname)                    url 与开始括号之间不能有空格
               相对url:   url(pathname) ex: pix/wattle22.gif
               样式表导入时候，@import url(special/toppings.css)会引入http://www.xxx.org/styles/special/toppings.css
               而我们期望引入的是http://www.xxx.org/special/toppings.css
##      关键字
               如 a:link {text-decoration: none;}中的none为关键字。
####         inherit
                    inherit是所有属性共有的，与其父元素的值相同。
                    toolbar a {color: inherit;} 这样让链接集成color的值，而不是代理默认值。一般默认继承规则优先级低于
                    指定规则，但是指定inherit则会把情况翻转。
##      CSS2单位
                    角度值：指定声音从哪个位置发出。共有3 种度：度deg/梯度grad/弧度rad.
                    时间值：用于指定元素之间的延迟。可表示为毫秒ms,也可为秒s.
                    频率值：语音浏览器可以产生声音声明一个给定频率。可以表示为Hz或者MHz.不区分大小写。
#第五章 字体
        CSS字体处理中最复杂的就是字体系列的匹配和字体加粗匹配，其次是字体大小的计算。
##      字体系列
              Serif 字体：字体成比例，其有上下短线。ex: Times/Georgia/New Century Schoolbook
              Sans-serif 字体：字体成比例，其上下无短线。ex: Helvetica/Geneva/Verdana/Arial/Univers
              Monospace 字体：字体不成比例。通常用来模仿打印机打印出来的文本。每个字符宽度完全相同。可能有上下短线也
                                可能没有短线。ex: Courier/Courier New/Andale Mono
              Cursive 字体：字体模仿人的手写体。ex: Zapf Chancery/Author/Comic Sans
              Fantasy 字体：无任何特征定义。ex: Western/Woodlock/Klingon
              特定字体系列：Times/Verdana/Helvetica/Arial
              用户安装的任何字体系列都会落入上述某种通用系列当中。
####        使用通用字体系列
                    如果希望文档中使用一种Sans-serif 字体，但是并不关心是那种：
                        body {font-family: sans-serif;}
####        指定字体系列
                        h1 {font-family: Georgia;}  如果用户代理没有此字体则使用默认字体显示
                        h1 {font-family: Georgia. serif;} 如果Georgia不可用则使用另外一种serif字体。
                        强烈建议所有的font-family规则中都提供一种通用字体系列。
####        使用引号
                     当字体名中有一个多个空格或者字体名包括%，#或$之类的符号，则需要使用引号ex: ‘Karrank%’
                     如果将一个通用名用引号包裹，则代理会热为你需要一个与此同名的字体，而不是一个通用字体系列。
                     单双引号都可以。
                     如果用于style 属性，此属性使用双引号，则字体必须使用单引号。
##      字体加粗
             a{ font-weight: normal|bold|lighter|100|200|300|400|500|600|700|800|900|inherit}
####        加粗如何起作用
                    400=normal
                    700=bold
####        让字体更粗 Need update
####        让字体更细 Need update
####        字体大小
                    *{font-size: xx-small| x-small| small| medium| large| x-large| xx-large| smaller| larger|<length>|
                                    percentage| inherit}        
                    初始值为：medium
                    其给定字体的em框提供一个大小，而不能保证实际显示字符就是这种大小。
####        绝对大小
                    一个绝对大小与下一个绝对大小之间的差别应当是向上1.5，向下0.66（缩放因子一般结余1.0~1.2之间CSS2）
####        相对大小
                    larger 和smaller 比较简单，其实相对父元素的大小，在绝对大小的梯度上上移或下移。使用绝对大小缩放因子
####        百分数和大小
                    总是跟父级元素的大小来计算。
####        字体大小和继承
                    font-size继承的是计算值而不是百分数。每次计算都有可能产生误差，如果计算丛集较多会积累误差。
####        使用长度单位
                    可以使用长度单位来设置字体的大小。
                    p.one {font-size：36pt;}
##      风格和变形
                    font-style 和font-variant
####        有风格的字体
                    *{font-style: italic| oblique| normal| inherit}
                    italic 是单独的字体
                    oblique是将现有字体倾斜
####        字体的变形
                    *{font-variant: small-caps| normal| inherit}
                    small-caps: 使用小型大写字母文本。大写字母大，小写字母是小的大写字母。
##      拉伸和调整字体
                    拉伸与替换
                    *{font-stretch: normal| wider| narrower| ultra-condensed| extra-condensed| condensed| semi-condensed
                                    expanded| extra-expanded| ultra-expanded| inherit}        
####        font属性
                    *{font: [[<font-style>||<font-variant>|| <font-weight>]?<font-size>[/<line-height>]?<font-family>] |
                     caption | icon | menu | message-box | small-caption | status-bar | inherit }
                     font 属性的前三个值（font-style, font-variant, font-weight）是可以不在乎顺序的。
                     而 font-size 和font-family则要按照特定的顺序。
####        增加行高
                     font设置了以上五个值之外还可以设置line-height,进过line-height是一个文本属性而不是字体属性。
                     这个可以作为font-size的一个补充用斜线（/）分割:
                                    body { font-size: 12px;}
                                    h2 {font: bold italic 200%/1.2 Verdana, Helvetica, Arial, Sans-serif;}
####        适当的使用简写
                     在使用font简写时所有的被忽略的值都会被重置为默认值。
####        使用系统字体
                     button {font: caption;}/*将button的字体设置为系统按钮的字体*/
                     caption: 用于标题的控件，如按钮；
                     icon: 用于对图标加标签；
                     menu: 用于菜单，即下拉菜单和菜单列表；
                     message-box：用于对话框；
                     small-caption: 用于对你小控件加标签；
                     status-bar：用于窗口状态条。
                     利用以上这些可以建立一些基于web的看似像系统自带的应用。
                     button{font:caption; font-size: 1em;}/*可以使字体大小跟其父元素保持一致。*/
##      字体匹配
                     page132
#第六章 文本属性
##      缩进和水平齐平
####        缩进文本
                    p{text-indent: <length>| <percentage> | inherit}无法用于行内元素，可用于块级元素。
                    行内元素使用内外边距
                    可以为负值，使首行悬挂在元素中余下部分的左边。（悬挂缩进）
                    p {text-indent: -4em; padding-left: 4em;}(防止悬挂部分超出浏览器窗口)
####        水平对齐
                    p {text-align: left | center | right | justify | inherit|}
                    center 与<center></center>元素相比，后者不仅影响文本还会把整个元素居中。
##      垂直对齐
####        行高
                    指定line-height可以用来增加或减少文本航之间的垂直间隔。line-height 的值和字体大小之差就是行间距。
                    p {line-height: <length> | <percentage> | <number> | normal | inherit}
####        构造文本行
                    p142
####        行高和继承
                    body {font-size: 10px;}
                    div {line-height:1em;}/*line height=10px*/
                    p {font-size:18px;}
                    ========================
                    指定一个数时，缩放因子将是继承值而不是计算值，这个数会应用到钙元素及其所有子元素。
                    ========================
                    body {font-size: 10px;}
                    div {line-height:1.5;}/*line height=18*1.5=27px*/
                    p {font-size:18px;}
####        垂直对齐文本
                    img {vertical-align: baseline | sub | super | top | text-top | middle | bottom| text-bottom |
                                            <percentage> | <length> | inherit} /*应用于行内元素*/
####        基线对齐
                    baseline
                    如果一个垂直对齐元素没有极限，也就是说这是一个图像或表单输入元素，或者其他替换元素，那么元素的底端
                    与其父元素的极限对齐。
####        上标和下标
                    sub | super
                    即升高或者降低文本基线或者图像底端。值取决于用户代理。
                    上标和下标并不改变字体的大小。
####        底端对齐
                    bottom
                    将元素的行内框底端与行框底端对齐
                    text-bottom
                    非文本元素会忽略这个值。
####        顶端对齐
                    top
                    与bottom相反。
####        居中对齐
                    middle
                    往往应用于图像，但不限于图像。
                    middle会把行内元素框的重点与父元素基线上方0.5ex处的一个点对齐，1ex相对于父元素的font-size定义。
####        百分数
                    使用百分数不能模仿图像的align = "middle" 对齐。正百分数会使元素升高，负百分数会使元素降低。
                     