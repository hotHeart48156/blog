serdes是英文serializer/deserializer的简称<br />在发送端多路低速并行信号转换成高速串行信号，经过传输后，在接收端高速串行型号转换为低速并行型号。  可以有效地减小传输信道和器件引脚，方便芯片信号同步。

在serders出现之前，信号同步主要是通过系统同步和源同步来传输数据的。

第一个是系统同步，第二个是源同步。<br />这两者不适用于高速信号同步。有着固有的缺陷。
<a name="Usryr"></a>
### 系统同步缺陷
有三个问题

1. 时钟信号到达两个芯片的时间不一样
2. 数据信号到达两个芯片的时间不一样
3. 时钟和数据的延迟不一样

所以这两种不适用于高速信号传输。<br />虽然可以通过芯片内部的PLL来补偿时钟延迟和数据延迟，但是。
<a name="DMqDv"></a>
### 源同步缺陷
TX把时钟和数据一起发送<br />时钟和数据保持相同的路径。<br />SSN（同步开关噪声）成为提高传输带宽的瓶颈。

![image.png](https://cdn.nlark.com/yuque/0/2024/png/580638/1712396753086-e545af0b-7330-4315-8e52-6e00231e18d4.png#averageHue=%23fafafa&clientId=u50d95f38-d11e-4&from=paste&height=579&id=u507b6c25&originHeight=724&originWidth=862&originalType=binary&ratio=1.25&rotation=0&showTitle=false&size=164079&status=done&style=none&taskId=u3c2b4ba4-d08f-4843-9b5a-eb60fa3b72f&title=&width=689.6)

<a name="ehj7Q"></a>
# Serders技术
<a name="KSSCW"></a>
#### 需要参考时钟

1. 需要在数据内内嵌时钟
2. 引脚少
3. 通过均衡技术实现长距离传输

数据采样差分传输<br />serders在TX端不传送直接的时钟信号，在RX端利用CDR电路从数据的边缘抽取时钟，并且找到最优采样位置。

