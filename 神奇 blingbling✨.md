♨️ 1. **[html]** 一键唤醒拔打电话、发送邮件、发送短信
```html
<a href="tel:188xxxxxxxx">一键拨打号码</a>
<a href="mailto:bettyxxxxxx@163.com">一键发送邮件</a>
<a href="sms:188xxxxxxx">一键发送短信</a>
```

🥑 2. **[css]** 消除 transition 闪屏
```css
.css { 
    -webkit-transform-style: preserve-3d; 
    -webkit-backface-visibility: hidden; 
    -webkit-perspective: 1000; 
} 
```
> transition 闪屏发生的情况：在 IOS 的 Safari 浏览器下，使用 transition 来进行动画变换时出现。
