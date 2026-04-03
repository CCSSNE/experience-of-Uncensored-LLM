# experience-of-Uncensored-LLM
大模型越狱经验交流

我的HF主页 https://huggingface.co/CCSSNE
我专门转存了很多未审核模型
防止作者下架或者是其他原因，但是最安全的还是存到自己的网盘或者是本地硬盘上

在国内的朋友推荐使用镜像下载站来下载
https://hf-mirror.com/

QQ交流群 1084838239 

为了防止本群爆炸，可以加一下这个禁言备用群
693742851
有条件的兄弟也可以加一下 Telegram 群组
https://t.me/+4pdsKLTS0N1lMDVl

一般推理用 .gguf 格式的量化 推荐使用q4km量化，基本没什么损失，体积减少两倍，相当于100b 的模型只占50g存储

自己也可以在 hf 上找未审查模型，这些是关键词
heretic  新的技术 效果很好
https://github.com/p-e-w/heretic

abliterated  这个带只带这个的基本上完蛋，是上一时代的技术
https://github.com/Sumandora/remove-refusals-with-transformers

https://github.com/FiditeNemini/mlx-abliteration

Uncensored 这个就是直译的未审查，但是并没有说是什么技术


专门做量化的 https://huggingface.co/mradermacher

以上是我觉得质量比较高的未审核模型作者
https://huggingface.co/llmfan46/models
https://huggingface.co/brayniac/models
https://huggingface.co/tvall43/models
https://huggingface.co/HauhauCS/models
https://huggingface.co/trohrbaugh/models


必须要拉黑的作者，典型的使用过时技术，而且粗制滥造，纯粹是图跑上来了事的,自己做出来的东西都不跑一下吗？
https://huggingface.co/huihui-ai
说实话他这样搞，然而他发一堆模型热度又高，很多人就下了他的，直接就觉得未审核大模型这条路是死路了，走不通了。。。

Windows 电脑和苹果上电脑，无脑推荐 lm studio，比ollama 好用太多，更加的直观，同样的设置，推理也快一些
不推荐 open web UI，占用资源太多了，如果你一定要用 api，那就用 cherry studio

n 卡记得在显示设置里面把那个显存回退策略改成倾向于不回退，这样才能基本上占满显存

开局就把 lm study 里面关于显存的安全策略全部关掉，然后通过调节 GPU 卸载层数，来手动分配

lm studio 的文件夹是嵌套的，必须一个文件夹里再套一个文件夹，它才识别的了

在模型设置页面，把这3个关掉，要不然容易加载失败，你清楚的明白他们是什么作用，而且硬件够用再开启
具体什么作用？建议问 AI 
将KV缓存卸载到GPU内存
保持模型在内存中
尝试mmap

天问3.5，如果没有官方的关闭思考，那就在，模型页面的Inference 最下方的模板添加一句
{%- set enable_thinking = false %}

其实就是这个 enable thinking 参数，如果你用其他软件有自定义字段或者 api 请求的时候，把这个请求带一下 false 就没有思考了。千万三点五的思考真的很恶心，他会思考一大堆，浪费很多算力
