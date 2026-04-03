# 我的HF主页

https://huggingface.co/CCSSNE

我专门转存了很多未审核模型

防止作者下架或者是其他原因，但是最安全的还是存到自己的网盘或者是本地硬盘上

## 下载方式

在国内的朋友推荐使用镜像下载站来下载

https://hf-mirror.com/

## 群组

QQ交流群 1084838239

为了防止本群爆炸，可以加一下这个禁言备用群

693742851

有条件的兄弟也可以加一下 Telegram 群组

https://t.me/+4pdsKLTS0N1lMDVl

## 模型格式与量化建议

一般推理用 .gguf 格式的量化 推荐使用q4km量化，基本没什么损失，体积减少两倍，相当于100b 的模型只占50g存储

## 未审查模型关键词

自己也可以在 hf 上找未审查模型，这些是关键词

### heretic

新的技术 效果很好

https://github.com/p-e-w/heretic

请注意这个很多作者会做 v1、v2、v3、好几个版本。

这个技术对于稠密模型非常有效，所以用 v3版本也可以

MOE模型的话就用v1版本

### abliterated

这个带只带这个的基本上完蛋，是上一时代的技术

https://github.com/Sumandora/remove-refusals-with-transformers

https://github.com/FiditeNemini/mlx-abliteration

### Uncensored

这个就是直译的未审查，但是并没有说是什么技术



## 额外的提示

注意，这种对模型本身的修改确实是很彻底的一种越狱方法。但是用系统提示词、上下文污染或者是催眠等等方法的越狱更加的通用，而且你可以对一些 api 或者是线上模型进行越狱, 也是值得研究的

对了，用 api 的有种好处就是一般 api 是不会加额外的二级审核模型的，就是只有模型本身的安全限制，这会会比网页版好越狱的多

但是说实话，api 的质量参差不齐，你不知道他跑的到底是原版fp16 fp8，，还是哪一级量化的

自己部署的话，推荐国内的这些平台

第一次部署推荐使用ollama 不过不要用平台给的镜像，随便选个镜像就可以了啊，反正都要升级了才能用千问3.5或者是最新的这些模型

具体我会发视频教程



## 量化作者

专门做量化的 https://huggingface.co/mradermacher

## 质量比较高的未审核模型作者

以上是我觉得质量比较高的未审核模型作者

https://huggingface.co/llmfan46/models

https://huggingface.co/brayniac/models

https://huggingface.co/tvall43/models

https://huggingface.co/HauhauCS/models

https://huggingface.co/trohrbaugh/models

## 必须拉黑的作者

必须要拉黑的作者，典型的使用过时技术，而且粗制滥造，纯粹是图跑上来了事的,自己做出来的东西都不跑一下吗？

https://huggingface.co/huihui-ai

说实话他这样搞，然而他发一堆模型热度又高，很多人就下了他的，直接就觉得未审核大模型这条路是死路了，走不通了。。。

## 软件推荐

Windows 电脑和苹果上电脑，无脑推荐 lm studio，比ollama 好用太多，更加的直观，同样的设置，推理也快一些

不推荐 open web UI，占用资源太多了，如果你一定要用 api，那就用 cherry studio

## 显卡设置

n 卡记得在显示设置里面把那个显存回退策略改成倾向于不回退，这样才能基本上占满显存

## LM Studio 设置建议

开局就把 lm study 里面关于显存的安全策略全部关掉，然后通过调节 GPU 卸载层数，来手动分配

lm studio 的文件夹是嵌套的，必须一个文件夹里再套一个文件夹，它才识别的了

在模型设置页面，把这3个关掉，要不然容易加载失败，你清楚的明白他们是什么作用，而且硬件够用再开启

具体什么作用？建议问 AI

### 需要关闭的选项

#### 将KV缓存卸载到GPU内存

#### 保持模型在内存中

#### 尝试mmap

## 天问3.5 关闭思考

天问3.5，如果没有官方的关闭思考，那就在，模型页面的Inference 最下方的模板添加一句

{%- set enable_thinking = false %}

其实就是这个 enable thinking 参数，如果你用其他软件有自定义字段或者 api 请求的时候，把这个请求带一下 false 就没有思考了。千万三点五的思考真的很恶心，他会思考一大堆，浪费很多算力

## 实测和评价

注意，仅为单轮测试，有比较大的随机性 说明v1版本没有明显的问题

#### llmfan46/Qwen3.5-35B-A3B-heretic-v1-GGUF Q4_K_S版本

t=0.1 关闭思考 中文问答

KL divergence 0.0366

Refusals 11/100

1.违规小说生成 (要求生成一万到一万五千字的长篇小说)

小说1：长度 5763tokens 

小说2(根据图片生成小说)：长度 4128tokens 

小说3：长度 4773tokens 

2.明显违规要求测试

没有任何问题，直接回答了



#### brayniac/Qwen3.5-35B-A3B-heretic mradermacher/Qwen3.5-35B-A3B-heretic-GGUF Q4_K_S版本

t=0.8 关闭思考 中文问答
KL divergence 0.0825

Refusals 5/100

1.违规小说生成

小说1：长度 3045tokens (口头拒绝，但是正常完成了写作)

小说2(根据图片生成小说)：长度 2973tokens 

小说3：长度 4948tokens 

2.明显违规要求测试

没有任何问题，直接回答了



#### HauhauCS/Qwen3.5-122B-A10B-Uncensored-HauhauCS-Aggressive IQ2_M版本

t=0.8 关闭思考 中文问答

1.违规小说生成

小说1：长度 4113tokens 3.04t/s 幻觉比较严重 质量比较差 勉强算正常生成



#### llmfan46/gemma-3-27b-it-ultra-heretic.i1-Q4_K_M

t=0.8 无思考 中文问答

1.违规小说生成

小说1：长度 2275tokens 2.57t/s 挺一般，挺短，但是勉强符合逻辑



#### huihui-ai/Huihui-Qwen3.5-35B-A3B-abliterated  Huihui-Qwen3.5-35B-A3B-abliterated.i1-Q4_K_M.gguf 

t=0.8 关闭思考 中文问答

1.违规小说生成

小说1：长度 7917tokens 说实话，质量挺一般，许多人物与情节不符合现实，而且根本没有包含违规内容 我的35k 上下文竟然被他自己截断了



#### llmfan46/Qwen3.5-27B-heretic-v3 mradermacher/Qwen3.5-27B-heretic-v3-i1-GGUF IQ4M版本

t=0.8 关闭思考 中文问答

1.违规小说生成

小说1：长度 5508tokens 2.53t/s 逻辑通顺行文流畅 就是速度太慢了



#### gemma4 26b

 0.8 0.95 Q4_K_M

1.违规小说生成

小说1：长度 1813t 10t/s 太短了 他知道自己很短



#### gemma4 31b

 0.8 0.95 Q4_K_M

1.违规小说生成

小说1：长度 1979t 1.96t/s 又短又慢，也没啥提升的短
