# Data Structure and Algorithm
# 预训练模型

## Attention Is All You Need

- ### Transformer网络结构

![image-20210508101114255](C:\Users\89791\AppData\Roaming\Typora\typora-user-images\image-20210508101114255.png)

​		整个网络结构由encoder和decoder两个部分组成。网络的输入是n个不同的向量$ (x_1,...,x_n)$，将其输入到encoder模块，**z** = $(z_1,...,z_n)$, 然后将 **z** 输入到decoder模块，每一次输出$(y_1,...,y_m)$ 中的一个向量，最终得到整个网络的输出。

​    	Encoder由6个完全相同的网络层组成，每个网络层包含一个multi-head self-attention mechanism和一个多层前馈神经网络层，这两个子网络层前面都有一个残差连接和layer normalization。

​    	Decoder也由6个完全相同的网络层组成，相对于encoder，其加入了一个encoder输出作为输入的multi-head self-attention mechanism。

- ### 注意力模块详解	

**Scaled Dot-Product Attention：**
  ![image-20210508103322277](C:\Users\89791\AppData\Roaming\Typora\typora-user-images\image-20210508103322277.png)

​        输入$Q \in (n,d_k), K \in (n,d_k), V \in (n,d_v)$ , 按照下面公式计算：

  ![image-20210508103621417](C:\Users\89791\AppData\Roaming\Typora\typora-user-images\image-20210508103621417.png)

​        首先用Q中的每个向量和K中的每个向量对应算内积，然后可以得到$n\times n$的数，组成一个大矩阵。然后用该矩阵和V相乘，得到n个输出的向量。具体计算如下图所示：

<img src="C:\Users\89791\AppData\Roaming\Typora\typora-user-images\image-20210508105322709.png" alt="image-20210508105322709" style="zoom: 50%;" />

**multi-head self-attention：**

​         将输入复制8份，进行线性变换，分别输入到**Scaled Dot-Product Attention**中进行计算，分别得到8组输出，再进行连接，合并。

​	     self-attention的含义是取Q，K，V相同。

![image-20210508103350695](C:\Users\89791\AppData\Roaming\Typora\typora-user-images\image-20210508103350695.png)
- ### Positional Encoding

  ​        由于transformer没有循环结构和卷积结构，为了可以充分利用序列的有序性，作者引入了positional encodings结构。如下图所示，$p_i$ 表示一个one-hot向量，用来对每个位置进行标记（论文中采用的向量是$e_i$ ，通过下面公式计算），在每个位置将输入向量和位置向量相加（等价于concatenate），再输入到SA模块中。

  ![image-20210508111343177](C:\Users\89791\AppData\Roaming\Typora\typora-user-images\image-20210508111343177.png)

<img src="C:\Users\89791\AppData\Roaming\Typora\typora-user-images\image-20210513115738895.png" alt="image-20210513115738895" style="zoom: 33%;" />



##  BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding



























