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