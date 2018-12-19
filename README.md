## 说明
音频输出为 `wav` 文件。

## 快速开始
方法一：
```
npm install swrecorder --save
```
```js
var swrecorder = require("swrecorder")
var recorder
swrecorder.get(function(rec) {
    recorder = rec
    recorder.start()
})
```
方法二：
1. 下载本仓库的 `index.js` 文件
2. 在项目中引用该 `js` 文件
3. 开始使用
```
var recorder
swrecorder.get(function(rec) {
    recorder = rec
    recorder.start()
})
```
**重要说明：必须通过调用 `swrecorder.get()` 方法，然后在回调函数里返回录音实例 `recorder`。所有方法都是挂在于 `recorder` 之上。**

## API 参考
1. `swrecorder.get(function(rec) {},config = {})` 

检查浏览器是否支持录音，并在回调函数里面返回录音实例 `recorder`。

`config` 配置音频参数：
> `sampleBits`: 采样位数（8或者16），默认为16位，
>
> `sampleRate`: 采样率（8000或16000），默认为16000

2. `recorder.start()`

开始录音，须在获取到录音实例之后调用。

```
var recorder
swrecorder.get(function(rec) {
    recorder = rec
    recorder.start()
})
```

3. `recorder.stop()`

停止录音。

4. `recorder.play(audio)`

播放文件，需要传入`audio`元素结点。

5. `recorder.upload(url,function (state, e){})`

以`FormData`形式上传文件，`url`为上传地址，回调函数中`state`返回上传状态，`e.target`返回上传结果。

`state`状态信息：

1. `uploading:` 正在上传
2. `ok:`        上传成功
3. `error:`     上传失败
4. `cancel:`    上传被取消


