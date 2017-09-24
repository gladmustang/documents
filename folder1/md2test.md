# <span style="color: rgb(226,80,65);">**translation.js**</span>

![undefined](https://camo.githubusercontent.com/593677694b40cafd0082dc2f670ae23935467666/68747470733a2f2f696d672e736869656c64732e696f2f7472617669732f53656c656374696f6e2d5472616e736c61746f722f7472616e736c6174696f6e2e6a732f6d61737465722e7376673f7374796c653d666c61742d737175617265)

translation.js 整合了[谷歌翻译](https://translate.google.cn/)、[百度翻译](https://fanyi.baidu.com/)与[有道翻译](http://fanyi.youdao.com/)的网页翻译接口，让你方便的在这些翻译接口之间切换，并获取相同数据结构的翻译结果。

## **特点**

### **可在 Node.js 及 Chrome 扩展/应用中使用**

translateion.js 能同时在 Node.js 和浏览器端运行，但由于浏览器端[同源策略](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS)的限制，这些网页接口只能在允许跨域的运行环境使用，Chrome 扩展/应用则是其中之一。

**注意**：为了能在 Chrome 扩展/应用中使用 translation.js，请阅读最后面的「在 Chrome 扩展/应用中使用」一节。

### **一致的参数与数据结构**

每个网页翻译的接口都有不同的参数和翻译结果，translation.js 统一了这些不同之处并提供了一致的 API，同时提供了每个接口的源数据方便自定义处理。

## **安装**

### **在 Node.js 或 Webpack（及类似的模块打包工具）中使用**

先用 NPM 安装：

npm install translation.js 

然后在代码中引用：

// CommonJS 中  

const tjs = require('translation.js')  

// ES6 中  

import * as tjs from 'translation.js'  

// 你也可以只引用你用得到的方法  

import { translate, detect, audio } from 'translation.js'

### **使用 <script> 标签**

在 Chrome 扩展/应用中使用 <script> 标签引用时，你需要先下载下面三个文件到你的项目里：

*   [superagent.js](https://unpkg.com/superagent/superagent.js)
*   [md5.min.js](https://unpkg.com/blueimp-md5/js/md5.min.js)
*   [translator.min.js](https://unpkg.com/translation.js/dist/translator.min.js)

然后在 HTML 中引用：

<!-- 先引用 translator.js 的依赖 -->  

<script src="path/to/superagent.js"></script>  

<script src="path/to/md5.min.js"></script>  

<!-- 然后引用 translator.js -->  

<script src="path/to/translator.min.js"></script>

然后就可以使用全局变量 window.tjs 调用方法了。

## **使用**

### **获取翻译结果**

获取一段文本的翻译结果可以用 translate() 方法：

tjs  

.translate('test')  

.then(result => {  

console.log(result) // result 的数据结构见下文  

})

其中 result 的结构示例如下：

{  

text: 'test', // 此次查询的文本  

raw: { ... }, // 接口返回的原本的数据  

link: '[https://translate.google.cn/#en/zh/test'](https://translate.google.cn/#en/zh/test'), // 在线翻译地址  

from: 'en', // 文本的源语种  

to: 'zh-CN', // 文本的目标语种  

// 单词的音标，目前只有用百度翻译英文单词才可能有  

phonetic: [  

{  

name: '美',  

ttsURI: '[https://fanyi.baidu.com/gettts?lan=en&text=test&spd=3&source=web'](https://fanyi.baidu.com/gettts?lan=en&text=test&spd=3&source=web'),  

value: 'test'  

},  

{  

name: '英',  

ttsURI: '[https://fanyi.baidu.com/gettts?lan=en-GB&text=test&spd=3&source=web'](https://fanyi.baidu.com/gettts?lan=en-GB&text=test&spd=3&source=web'),  

value: 'test'  

}  

],  

// 单词的详细释义，翻译英文单词时才可能有  

dict: 'n. 试验；测验；考验；化验', 'vt. 测验；考验；考查；勘探', 'vi. 受试验；受测验；受考验；测得结果' ,  

// 一般翻译结果，数组里的每一项是一个段落的翻译  

result: '测试'  

}

**注意**：translation.js 统一使用 [ISO-639-1 标准](https://zh.wikipedia.org/wiki/ISO_639-1)作为语种格式，任何地方出现的语种都遵循这个标准。

翻译结果默认来自谷歌翻译，你也可以指定要从哪个接口获取结果：

tjs.translate({  

text: 'test',  

api: 'youdao' // 从有道翻译获取结果，或者设为 'baidu' 从百度翻译获取  

})

### **检测语种**

检测一段文本的语种可以使用 detect() 方法：

tjs  

.detect('test')  

.then(lang => {  

console.log(lang) // => 'en'  

})

默认情况下，语种检测的数据同样来自谷歌翻译，但你同样可以指定其他接口：

tjs.detect({  

text: 'test',  

api: 'youdao' // 从有道翻译获取结果，或者设为 'baidu' 从百度翻译获取  

})

**注意**：建议一直使用谷歌翻译检测语种，因为它支持的语种是最多的，其他接口可能不支持你所检测的文本的语种。

### **获取文本的语音朗读地址**