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
            h1, h2, h3, h4, h5, h6,{color: gray; background: white; padding: 0.5em; border: 1px solid black; forn-family: Charcoal, sans-serif;}
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
            .warning.urgent {background: silver} /*同时属于warning和urgent类的元素背景被设置为silver，假如有三个类，但是这三个类包好了warning，urgent,那么这个元素也会被设置为silver*/
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
            
