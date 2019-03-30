#96NIST_to_CIFAR10_to_recg_CAPTCHA

  最近想把神经网络应用于爬虫的验证码识别，从分类角度着手的话，上学期实践过的mnist和cifar10可作为自定义图片数据集比较好的一个参考<br>
  这次打算用一个自己标注的数据集进行实验，网络结构和mnist一样。<br>
  但是！！！！自己制作数据集的话需要很多精力。。mnist都上万级别的图片。。标注起来emmm。。实在不行我就去跟别人要个数据集吧(✿◡‿◡)
<br>
## 这里打算分三个部分进行：先放MNIST卷积的代码，再放CIFAR-10卷积的代码，最后再进行卷积网络识别验证码
<br>
顺便也把mnist的卷积实现放到github（经过软工老师的引导，我发现自己开始喜欢上github这个代码托管网站了）
**********************
            
         ps：我之后会逐渐把以前实现过的项目都贴到github上，以前不怎么用github，但是放在文件夹里也是放着，放在github也是放着，不如放到github上来托管，保证不会丢失

<br>

### First
闲着没事，这里记录一下我对mnist数据集的卷积实现的几个要点：<br>
1、简单粗暴，两层卷积+两层全连接+dropout（本来想又用正则化又drpout的，但是发现效果比单用一个稍差）<br>
2、训练结束后，由于我的笔记本gpu配置不高（Geforce 920。。。。。。。反正能用就行），最后使用测试集进行精度测试时，若直接把整个mnist.test.image都喂进      去，会使显存溢出；于是我换了个方法：对10000张测试图片进行分批操作，对每一个batch（设一个batch_size）进行分类正确的数目统计，最后求和，再百分数即可<br>
3、模型的保存，使用：我设置了一个is_train标志位，True的话表示进行训练，False则表示模型使用

### 结果：精度达到96%（训练5000次的结果）

*************************

### Second
CIFAR-10的卷积实现：<br>
1、两层卷积+三层全连接+dropout；
2、数据的导入有点迷，官方的读入image数据和类标数据的方法是不同的；
3、精度最后只有69%，查了了一下官方最高记录86%

### Third
验证码图片识别的卷积实现：
更新：这事先缓缓吧。。。
