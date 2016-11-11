# 基于Web Audio API实现音频可视化效果



要从你的音频源获取数据，你需要一个 [`AnalyserNode`](https://developer.mozilla.org/zh-CN/docs/Web/API/AnalyserNode)节点，它可以用 [`AudioContext.createAnalyser()`](https://developer.mozilla.org/zh-CN/docs/Web/API/AudioContext/createAnalyser) 方法创建，比如：

```
<audio id="myAudio" src="try.mp3" controls="controls"></audio>
--------------------------------------------------------------------
var audioCtx = new (window.AudioContext || window.webkitAudioContext)();
var audio = document.getElementById('myAudio');//获取音频的dom节点

var audioSrc = audioCtx.createMediaElementSource(audio);//获取音频数据
var analyser = audioCtx.createAnalyser();//创建存放音频数据的节点
audioSrc.connect(analyser);//链接数据和节点
```

分析器节点(Analyser Node) 将在一个特定的频率域里使用[快速傅立叶变换](https://zh.wikipedia.org/wiki/%E5%BF%AB%E9%80%9F%E5%82%85%E9%87%8C%E5%8F%B6%E5%8F%98%E6%8D%A2)(Fast Fourier Transform (FFT) )来捕获音频数据，这取决于你给 [`AnalyserNode.fftSize`](https://developer.mozilla.org/zh-CN/docs/Web/API/AnalyserNode/fftSize) 属性赋的值（如果没有赋值，默认值为2048）。

> 这些方法把数据复制进了一个特定的数组当中，所以你在调用它们之前要先创建一个新数组,
>
> 你可以使用用一个 [`Float32Array`](https://developer.mozilla.org/zh-CN/docs/Web/API/Float32Array) 或者 [`Uint8Array`](https://developer.mozilla.org/zh-CN/docs/Web/API/Uint8Array) 数组，具体需要哪个视情况而定
>

看个例子，比如我们正在处理一个2048尺寸的FFT。我们返回 [`AnalyserNode.frequencyBinCount`](https://developer.mozilla.org/zh-CN/docs/Web/API/AnalyserNode/frequencyBinCount) 值，它是FFT的一半，然后调用Uint8Array()，把frequencyBinCount作为它的长度参数 —— 这代表我们将对这个尺寸的FFT收集一半的多少数据点

```
analyser.fftSize = 2048;
var bufferLength = analyser.frequencyBinCount;
var dataArray = new Uint8Array(bufferLength);
```

#### 要捕获数据：

用 [`AnalyserNode.getFloatFrequencyData()`](https://developer.mozilla.org/zh-CN/docs/Web/API/AnalyserNode/getFloatFrequencyData) 或 [`AnalyserNode.getByteFrequencyData()`](https://developer.mozilla.org/zh-CN/docs/Web/API/AnalyserNode/getByteFrequencyData) 方法来获取频率数据

用[`AnalyserNode.getByteTimeDomainData()`](https://developer.mozilla.org/zh-CN/docs/Web/API/AnalyserNode/getByteTimeDomainData) 或 [`AnalyserNode.getFloatTimeDomainData()`](https://developer.mozilla.org/zh-CN/docs/Web/API/AnalyserNode/getFloatTimeDomainData) 来获取波形数据

要正确检索数据并把它复制到我们的数组里，就要调用我们想要的数据收集方法，把数组作为参数传递给它，例如：

```
analyser.getByteTimeDomainData(dataArray);
```

现在我们就获取了那个时间域上的音频数据，并存到了我们的数组里，而且可以把它做成我们喜欢的可视化效果了，比如把它画在一个HTML5 [`canvas`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/canvas)画布上。

#### 至于canvas方面的内容可参考[基于Web Audio API实现音频可视化效果](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Audio_API/Visualizations_with_Web_Audio_API)

#### 亦可参考github上[vudio.js插件](https://github.com/margox/vudio.js)，内部有完整demo



