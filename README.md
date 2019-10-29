# 环保设施智能检测PC端管理系统

#### 介绍
环保设施智能检测PC端管理系统


#### 开发注意事项
1. baseUrlConfig 该文件用来配置接口地址 与config.js中的layui.define中配置的BASEURL功能相同，如果要改变接口路径，则这两个地方都需要修改
2. common.css 为公共样式，开发的时候将自己需要用到的公共样式放在以自己名字注释的代码块中，提交代码的时候不要提交，只留在本地开发测试，最后统一合并提交。
	【注意】: 在给common.css中书写类名的时候，将自己名字的首字母作为前缀防止合并后样式覆盖。 例：l-card-title 、c-card-title 、z-card-title


#### 开发中页面跳转

如果需要页面间的跳转，比如'实时监测'中点击'当前在线企业'就会跳转到设备状态列表。关于跳转的源码在admin.js 766行。
简易操作：在按钮点击事件中执行左侧菜单点击事件，直接调用admin.js中的方法。
代码： window.parent.document.getElementById("自己在左侧菜单中目标页面的a链接中加一个ID").click(); 

#### 接口异常处理方式

统一用这个弹窗提示出来异常信息
vm.$notify.error({
	title: '错误',
	message: res.data.msg
})

#### axios使用body传值

axios({
	method: "post",
	url: BASEURL,
	data: {
	    
	},
	headers: {
	    "Content-Type": "application/json;charset=UTF-8"
	}
}).then(function (res) {
	if (res.data.code == 0) {
	    
	} else {
	    vm.$notify.error({
	        title: '错误',
	        message: res.data.msg
	    });
	}
})