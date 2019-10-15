`⚠️ 注意：` 用做网站图标的图片文件选`ico`类型，文件名最好统一命名 `favicon.ico`

- ico 图标在线制作：[http://www.faviconico.org](http://www.faviconico.org)

## 步骤：
1. 将 favicon 图片放到 `static` 文件夹下

    > 用 vue-cli 搭建的Vue项目。
    
2. 然后在 `index.html` 中添加：
    ```html
    <link rel="shortcut icon" type="image/x-icon" href="static/favicon.ico">
    ```
    > ` rel="shortcut icon"`：字符串将被多数遵守标准的浏览器识别为列出可能的关键词（“shortcut”将被忽略，而仅适用“icon”）； 加上 `shortcut` 是为了适配 IE 浏览器。
    `type="image/x-icon"`：格式必须是 png 或者 ico。

而Internet Explorer将会把它作为一个单独的名称（“shortcut icon”）。 
这样做的结果是所有浏览器都可以理解此代码。 
————————————————
版权声明：本文为CSDN博主「fei2636」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/fei2636/article/details/81116838
    
3. 刷新浏览器页面。


<br><br>

🔗 参考链接：
- [Vue项目 -- favicon设置以及动态修改favicon](https://www.cnblogs.com/chinabin1993/p/8509743.html)
