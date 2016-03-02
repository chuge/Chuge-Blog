title: Iframe跨域嵌套页面
date: 2016-02-19 18:40:05
tags:
---

----------------------

### 遇到的问题

手机端，在父页面内嵌跨域iframe的实践， 关于fixed失效和devicemotion失效 与第三方客户某微，需要交互。应对方要求，他们提供父级页面，然后用iframe跨域引用我们的页面。

### 1.计算子页面高度

把问题分解，第一个要解决的是iframe引入的页面高度不等，需要在子页面加载完，计算子页面的高度后调整iframe的高度。

		var resizeHeight = (function() {
		        var heightCalculated;

		        return function(target, iframeHeight) {
		            //only reset height when height is not initialized and not equal to previous calculated
		            if (!heightCalculated || (!!heightCalculated && iframeHeight !== heightCalculated)) {
		                $(target).height(iframeHeight);
		                heightCalculated = iframeHeight;
		            }
		        };
		    })();

		    $('iframe').unbind('load').load(function(){
		    var target = this;
		    var iframeHeight = target.contentWindow.document.body.scrollHeight;
		    resizeHeight(target, iframeHeight);
		    setInterval(function(){
		        resizeHeight(target, iframeHeight);
		    }, 100);
		});

### 2.fixed在iframe中“失效”

因为子页面的fixed元素是相对于子页面定位的，而我们滚动的滚动条是父级页面的。 解决方案是通过监听滚动条事件或者设置一个较小时间的轮询，来检测当前父页面的滚动条的scrollTop,也就是滚动条往下滚动了多少，然后在子页面中获取当前父页面的scrollTop，根据可视区域的高度window.innerHeight，去计算子页面fixed元素的位置。

### 3.跨域问题

这种方案当父页面和子页面在同域名下是没有问题的，但当父子页面不在同一个域名下，互相不能调用各自window里面的属性。这时候就要通过使用HTML5的新API，postmessage去解决。

#### a.父页面可以如下方式发送

		document.querySelector('iframe').contentWindow.postMessage({
		            source:'fff',
		            type:'parentInfo',
		            parentHeight:window.innerHeight,
		            parentScrollY:window.scrollY
		        },'http://192.168.190.133');

#### b.子页面可以如下方式发送

		window.parent.postMessage({
                source:'www.duiba.com.cn',
                viewport:'DPI'
            }, 'http://192.168.1.133');

#### c.监听postmessage

		window.addEventListener("message", function(event) {
                    if(event.data.source=='fff' && event.data.type=='parentInfo'){
                        $('.win-modal .modal-dialog').css({
                            top: event.data.parentScrollY + event.data.parentHeight / 2
                        });
                    }
                },false);
