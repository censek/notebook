♨️ 1. **[html]** 一键唤醒拔打电话、发送邮件、发送短信
```html
<a href="tel:188xxxxxxxx">一键拨打号码</a>
<a href="mailto:bettyxxxxxx@163.com">一键发送邮件</a>
<a href="sms:188xxxxxxx">一键发送短信</a>
```
<br>

🥑 2. **[css]** 消除 transition 闪屏
```css
.css { 
    -webkit-transform-style: preserve-3d; 
    -webkit-backface-visibility: hidden; 
    -webkit-perspective: 1000; 
} 
```
> transition 闪屏发生的情况：在 IOS 的 Safari 浏览器下，使用 transition 来进行动画变换时出现。

<br>

🥑 3. **[css]** webp 图片格式 <Br>
- [探究 WebP 一些事儿](https://aotu.io/notes/2016/06/23/explore-something-of-webp/)
    
```shell
#（1）使用 homebrew 安装 webp 工具
brew install webp
# (2) 安装完命令行工具后，就可以使用 cwebp 将 JPG 或 PNG 图片转换成 WebP 格式。
cwebp [-preset <...>] [options] in_file [-o out_file]
# (3) 也可以使用 dwebp 将 WebP 图片转换回 PNG 图片（默认）。
dwebp in_file [options] [-o out_file]
```
> options 参数列表中包含质量参数 `q`，q 为 `0～100` 之间的数字，比较典型的质量值大约为 80。<br>

🌰：`cwebp -q 80 111.jpeg -o 222.webp`

<img src="https://img-blog.csdnimg.cn/20191216143334376.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0J1bGVfZGF6ZQ==,size_16,color_FFFFFF,t_70" width="500px">
<br>

🥑 4. **[css]** web 安全色 <br>
- [https://www.bootcss.com/p/websafecolors/](https://www.bootcss.com/p/websafecolors/)<br>
    在不同的平台展示的效果和预期一致。<br>
    WEB 安全色的 `RGB` 值均为 `51` 的倍数。`rgb(0,0,51)`, `rgb(0,0,102)`, `rgb(0,0,153)` 都是 web 安全色。
<br>

🥑 5. **[html]** 分区响应图 <Br>
    分区响应图，就是当超链接按钮是图片时，将图片进行划分，使得点击图片不同区域时，会有不同的反馈。<br>
    🌰：
    ```html
      <img src="./1.png" usemap="#myMap" />
      <map name="myMap">
        <area href="http://baidu.com" shape="rect" coords="50,106,220,273" />
        <area href="http://google.com" shape="rect" coords="260,106,430,275" />
        <area href="http://juejin.im" shape="default" />
      </map>
    ```
