#多说评论区显示UA与博主标示
> 多说和Disqus是现在大多数博主喜欢使用的评论插件，这里总结了一下新版多说怎样显示浏览器信息与操作系统信息（UA），以及博主的标示。

首先给大家看一下效果图，动态效果和详细情况可以查看本楼底部的评论去。
<img src="/img/dsUA/01.png" />
### 1、添加头像旋转CSS与排版样式。

操作步骤很简单，登录多说->后台管理->设置->基本设置->自定义CSS。
```cpp
/*Head Start*/
#ds-thread #ds-reset ul.ds-comments-tabs li.ds-tab a.ds-current {
    border: 0px;
    color: #6D6D6B;
    text-shadow: none;
    background: #F3F3F3;
}

#ds-thread #ds-reset .ds-highlight {
    font-family: Microsoft YaHei, "Helvetica Neue", Helvetica, Arial, Sans-serif;;
    font-size: 100%;
    color: #6D6D6B !important;
}

#ds-thread #ds-reset ul.ds-comments-tabs li.ds-tab a.ds-current:hover {
    color: #696a52;
    background: #F2F2F2;
}

#ds-thread #ds-reset a.ds-highlight:hover {
    color: #696a52 !important;
}

#ds-thread {
    padding-left: 30px;
}

#ds-thread #ds-reset li.ds-post, #ds-thread #ds-reset #ds-hot-posts {
    overflow: visible;
}

#ds-thread #ds-reset .ds-post-self {
    padding: 10px 0 10px 10px;
}

#ds-thread #ds-reset li.ds-post, #ds-thread #ds-reset .ds-post-self {
    border: 0 !important;
}

#ds-reset .ds-avatar, #ds-thread #ds-reset ul.ds-children .ds-avatar {
    top: 15px;
    left: -20px;
    padding: 5px;
    width: 36px;
    height: 36px;
    box-shadow: -1px 0 1px rgba(0, 0, 0, .15) inset;
    border-radius: 46px;
    background: #FAFAFA;
}

#ds-thread .ds-avatar a {
    display: inline-block;
    padding: 1px;
    width: 32px;
    height: 32px;
    border: 1px solid #b9baa6;
    border-radius: 50%;
    background-color: #fff !important;
}

#ds-thread .ds-avatar a:hover {
}

#ds-thread .ds-avatar > img {
    margin: 2px 0 0 2px;
}

#ds-thread #ds-reset .ds-replybox {
    box-shadow: none;
}

#ds-thread #ds-reset ul.ds-children .ds-replybox.ds-inline-replybox a.ds-avatar,
#ds-reset .ds-replybox.ds-inline-replybox a.ds-avatar {
    left: 0;
    top: 0;
    padding: 0;
    width: 32px !important;
    height: 32px !important;
    background: none;
    box-shadow: none;
}

#ds-reset .ds-replybox.ds-inline-replybox a.ds-avatar img {
    width: 32px !important;
    height: 32px !important;
    border-radius: 50%;
}

#ds-reset .ds-replybox a.ds-avatar,
#ds-reset .ds-replybox .ds-avatar img {
    padding: 0;
    width: 50px !important;
    height: 50px !important;
    border-radius: 5px;
}

#ds-reset .ds-avatar img {
    width: 32px !important;
    height: 32px !important;
    border-radius: 32px;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.22);
    -webkit-transition: .8s all ease-in-out;
    -moz-transition: .4s all ease-in-out;
    -o-transition: .4s all ease-in-out;
    -ms-transition: .4s all ease-in-out;
    transition: .4s all ease-in-out;
}

.ds-post-self:hover .ds-avatar img {
    -webkit-transform: rotateX(360deg);
    -moz-transform: rotate(360deg);
    -o-transform: rotate(360deg);
    -ms-transform: rotate(360deg);
    transform: rotate(360deg);
}

#ds-thread #ds-reset .ds-comment-body {
    -webkit-transition-delay: initial;
    -webkit-transition-duration: 0.4s;
    -webkit-transition-property: all;
    -webkit-transition-timing-function: initial;
    background: #F7F7F7;
    padding: 15px 15px 15px 47px;
    border-radius: 5px;
    box-shadow: #B8B9B9 0 1px 3px;
    border: white 1px solid;
}

#ds-thread #ds-reset ul.ds-children .ds-comment-body {
    padding-left: 15px;
}

#ds-thread #ds-reset .ds-comment-body p {
    color: #787968;
}

#ds-thread #ds-reset .ds-comments {
    border-bottom: 0px;
}

#ds-thread #ds-reset .ds-powered-by {
    display: none;
}

#ds-thread #ds-reset .ds-comments a.ds-user-name {
    font-weight: normal;
    color: #3D3D3D !important;
}

#ds-thread #ds-reset .ds-comments a.ds-user-name:hover {
    color: #D32 !important;
}

#ds-thread #ds-reset #ds-bubble {
    display: none !important;
}

#ds-thread #ds-reset #ds-hot-posts {
    border: 0;
}

#ds-reset #ds-hot-posts .ds-gradient-bg {
    background: none;
}

#ds-thread #ds-reset .ds-comment-body:hover {
    background-color: #F1F1F1;
    -webkit-transition-delay: initial;
    -webkit-transition-duration: 0.4s;
    -webkit-transition-property: all;
    -webkit-transition-timing-function: initial;
}

#ds-smilies-tooltip ul.ds-smilies-tabs {
    height: 139px;
!important;
}

@media screen and  (max-width: 768px) {
    #ds-reset form {
        padding-left: 25px;
    }
}

/*Head End*/
```
添加完CSS即可实现上面效果图的样式，想要自定义的话可以查看官方文档并借助审查元素来自己设计。
### 2、本地化embed.js文件
(1)下载多说官方新版embed.js：[http://static.duoshuo.com/embed.js](http://static.duoshuo.com/embed.js)
(2)下载完成后把下列JS代码插入官方代码的最上方。
```js
//More info: http://blog.isnomo.com/2016/12/06/多说评论区显示UA标示/
//移动客户端判断开始
function checkMobile() {
    var isiPad = navigator.userAgent.match(/iPad/i) != null;
    if (isiPad) {
        return false;
    }
    var isMobile = navigator.userAgent.match(/iphone|android|phone|mobile|wap|netfront|java|opera mobi|opera mini|ucweb|windows ce|symbian|symbianos|series|webos|sony|blackberry|dopod|nokia|samsung|palmsource|xda|pieplus|meizu|midp|cldc|motorola|foma|docomo|up.browser|up.link|blazer|helio|hosin|huawei|novarra|coolpad|webos|techfaith|palmsource|alcatel|amoi|ktouch|nexian|ericsson|philips|sagem|wellcom|bunjalloo|maui|smartphone|iemobile|spice|bird|zte-|longcos|pantech|gionee|portalmmm|jig browser|hiptop|benq|haier|^lct|320x320|240x320|176x220/i) != null;
    if (isMobile) {
        return true;
    }
    return false;
}
//移动客户端判断结束
//管理员判断开始
function sskadmin(r) {
    var ssk = '';
    // console.log(r);
    if ( r == 6261430928132801282) {
        if (checkMobile()) {
            ssk = '<span class="ua"><span class="sskadmin">博主</span></span>';
        } else {
            ssk = '<span class="ua"><span class="sskadmin">博主</span></span>';
        }
    } else {
        if (checkMobile()) {
            ssk = '<br><br>';
        }
    }
    return ssk;
}

//管理员判断结束
//显UA开始
function sskua(e) {
    var r = new Array;
    var outputer = '';
    if (r = e.match(/FireFox\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_firefox"><i class="fa fa-firefox"></i> FireFox'
    } else if (r = e.match(/Maxthon([\d]*)\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_maxthon"><i class="fa fa-globe"></i> Maxthon'
    } else if (r = e.match(/BIDUBrowser([\d]*)\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_ucweb"><i class="fa fa-globe"></i> 百度浏览器'
    } else if (r = e.match(/UBrowser([\d]*)\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_ucweb"><i class="fa fa-globe"></i> UCBrowser'
    } else if (r = e.match(/UCBrowser([\d]*)\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_ucweb"><i class="fa fa-globe"></i> UCBrowser'
    } else if (r = e.match(/MetaSr/ig)) {
        outputer = '<span class="ua_sogou"><i class="fa fa-globe"></i> 搜狗浏览器'
    } else if (r = e.match(/2345Explorer/ig)) {
        outputer = '<span class="ua_2345explorer"><i class="fa fa-globe"></i> 2345王牌浏览器'
    } else if (r = e.match(/2345chrome/ig)) {
        outputer = '<span class="ua_2345chrome"><i class="fa fa-globe"></i> 2345加速浏览器'
    } else if (r = e.match(/LBBROWSER/ig)) {
        outputer = '<span class="ua_lbbrowser"><i class="fa fa-globe"></i> 猎豹安全浏览器'
    } else if (r = e.match(/MicroMessenger\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_qq"><i class="fa fa-weixin"></i> 微信'
        /*.split('/')[0]*/
    } else if (r = e.match(/QQBrowser\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_qq"><i class="fa fa-qq"></i> QQ浏览器'
        /*.split('/')[0]*/
    } else if (r = e.match(/QQ\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_qq"><i class="fa fa-qq"></i> QQ浏览器'
        /*.split('/')[0]*/
    } else if (r = e.match(/MiuiBrowser\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_mi"><i class="fa fa-globe"></i> Miui浏览器'
        /*.split('/')[0]*/
    } else if (r = e.match(/Chrome([\d]*)\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_chrome"><i class="fa fa-chrome"></i> Chrome'
        /*.split('.')[0]*/
    } else if (r = e.match(/safari\/([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_apple"><i class="fa fa-safari"></i> Safari'
    } else if (r = e.match(/Opera[\s|\/]([^\s]+)/ig)) {
        var r1 = r[0].split("/");
        outputer = '<span class="ua_opera"><i class="fa fa-opera"></i> Opera'
    } else if (r = e.match(/Trident\/7.0/gi)) {
        outputer = '<span class="ua_ie"><i class="fa fa-internet-explorer"></i> IE 11'
    } else if (r = e.match(/MSIE\s([^\s|;]+)/gi)) {
        outputer = '<span class="ua_ie"><i class="fa fa-internet-explorer"></i> IE' + ' ' + r[0]
        /*.replace('MSIE', '').split('.')[0]*/
    } else {
        outputer = '<span class="ua_other"><i class="fa fa-globe"></i> 其它浏览器'
    }
    if (checkMobile()) {
        Mobile = '<br><br>';
    } else {
        Mobile = '';
    }
    return outputer + "</span>" + Mobile;
}
function sskos(e) {
    var os = '';
    if (e.match(/win/ig)) {
        if (e.match(/nt 5.1/ig)) {
            os = '<span class="os_xp"><i class="fa fa-windows"></i> Windows XP'
        } else if (e.match(/nt 6.1/ig)) {
            os = '<span class="os_7"><i class="fa fa-windows"></i> Windows 7'
        } else if (e.match(/nt 6.2/ig)) {
            os = '<span class="os_8"><i class="fa fa-windows"></i> Windows 8'
        } else if (e.match(/nt 6.3/ig)) {
            os = '<span class="os_8_1"><i class="fa fa-windows"></i> Windows 8.1'
        } else if (e.match(/nt 10.0/ig)) {
            os = '<span class="os_8_1"><i class="fa fa-windows"></i> Windows 10'
        } else if (e.match(/nt 6.0/ig)) {
            os = '<span class="os_vista"><i class="fa fa-windows"></i> Windows Vista'
        } else if (e.match(/nt 5/ig)) {
            os = '<span class="os_2000"><i class="fa fa-windows"></i> Windows 2000'
        } else {
            os = '<span class="os_windows"><i class="fa fa-windows"></i> Windows'
        }
    } else if (e.match(/android/ig)) {
        os = '<span class="os_android"><i class="fa fa-android"></i> Android'
    } else if (e.match(/ubuntu/ig)) {
        os = '<span class="os_ubuntu"><i class="fa fa-desktop"></i> Ubuntu'
    } else if (e.match(/linux/ig)) {
        os = '<span class="os_linux"><i class="fa fa-linux"></i> Linux'
    } else if (e.match(/mac/ig)) {
        os = '<span class="os_mac"><i class="fa fa-apple"></i> Mac OS X'
    } else if (e.match(/unix/ig)) {
        os = '<span class="os_unix"><i class="fa fa-desktop"></i> Unix'
    } else if (e.match(/symbian/ig)) {
        os = '<span class="os_nokia"><i class="fa fa-mobile"></i> Nokia SymbianOS'
    } else {
        os = '<span class="os_other"><i class="fa fa-desktop"></i> 其它操作系统'
    }
    return os + "</span>";
}
//显UA结束
```
> 把19行 r == 6261430928132801282 后面的数字替换为自己的多说ID。

自己ID查看方法：登录多说->个人资料->点击自己的名字，浏览器地址栏即为自己的多说ID。
<img src="/img/dsUA/02.png" />
替换完成后，搜索 `u(r.name) + "</span>"),` 在它的后面添加代码下列代码：
```js
t += "<span class=\"ua\">" + sskadmin(r.user_id) + "</span><span class=\"ua\">" + sskua(s.agent) + "</span><span class=\"ua\">" + sskos(s.agent) + "</span>",
```
添加后此段代码前应为 `u(r.name) + "</span>"),` 此段代码后为 `t += "</div>", 1 == i.max_depth` 请注意插入代码的位置，此处容易出错。
### 3、添加UA与博主标示的CSS
按照插入头像CSS的方法接着插入显示UA标示的CSS。
```cpp
/*UA Start*/
span.ua {
    margin: 0 1px!important;
    color: #FFFFFF!important;
    /*text-transform: Capitalize!important;
    float: right!important;
    line-height: 18px!important;*/;
}

.ua_other.os_other {
    background-color: #ccc!important;
    color: #fff;
    border: 1px solid #BBB!important;
    border-radius: 4px;
}

.ua_ie {
    background-color: #428bca!important;
    border-color: #357ebd!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_firefox {
    background-color: #f0ad4e!important;
    border-color: #eea236!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_maxthon {
    background-color: #7373B9!important;
    border-color: #7373B9!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_ucweb {
    background-color: #FF740F!important;
    border-color: #d43f3a!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_sogou {
    background-color: #78ACE9!important;
    border-color: #4cae4c!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_2345explorer {
    background-color: #2478B8!important;
    border-color: #4cae4c!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_2345chrome {
    background-color: #F9D024!important;
    border-color: #4cae4c!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_mi {
    background-color: #FF4A00!important;
    border-color: #4cae4c!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_lbbrowser {
    background-color: #FC9D2E!important;
    border-color: #4cae4c!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_chrome {
    background-color: #EE6252!important;
    border-color: #4cae4c!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_qq {
    background-color: #3D88A8!important;
    border-color: #4cae4c!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_apple {
    background-color: #E95620!important;
    border-color: #4cae4c!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.ua_opera {
    background-color: #d9534f!important;
    border-color: #d43f3a!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.os_vista,.os_2000,.os_windows,.os_xp,.os_7,.os_8,.os_8_1 {
    background-color: #39b3d7!important;
    border-color: #46b8da!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.os_android {
    background-color: #98C13D!important;
    border-color: #01B171!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.os_ubuntu {
    background-color: #DD4814!important;
    border-color: #01B171!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.os_linux {
    background-color: #3A3A3A!important;
    border-color: #1F1F1F!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.os_mac {
    background-color: #666666!important;
    border-color: #1F1F1F!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.os_unix {
    background-color: #006600!important;
    border-color: #1F1F1F!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.os_nokia {
    background-color: #014485!important;
    border-color: #1F1F1F!important;
    border-radius: 4px;
    padding: 0 5px!important;
}

.sskadmin {
    background-color: #00a67c!important;
    border-color: #01B171!important;
    border-radius: 4px;
    padding: 0 5px!important;
}
/*UA End*/
```
> 至此多说评论区已经可以显示UA与博主标示，并带有头像旋转样式。
想偷懒的同学可以下载我做好的 [embed_ua.js](/img/down/embed_ua.js)，修改多说ID即可使用。
我把需要添加的CSS都集合在一个文件里方便大家添加：[多说自定义CSS下载](/img/down/dsUA.css)