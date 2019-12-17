## Word Embedding
Reference: [word embedding and word2vec](https://towardsdatascience.com/introduction-to-word-embedding-and-word2vec-652d0c2060fa)
[word2vec parameter learning explained](https://arxiv.org/pdf/1411.2738.pdf)
### 引例
设想一下这样一个场景：
Have a good day
Have a great day
如果我们用one-hot对这两句话编码["have", "a", "good", "great", "day"] -> "good"[0,0,1,0,0]和"great"[0,0,0,1,0]之间的距离与"have"[1,0,0,0,0]和"day"[0,0,0,0,1]的距离是一样的，这显然不合理。
我们需要使得这样两个词之间的cosine距离接近1
### word embedding思路
- word embedding -> 就是将语言空间嵌入到数学空间
- word embedding -> 降维
- representation
	- one-hot representation
		- 认为所有的词都是独立的
		- 维数灾难
		- 词汇鸿沟
	- distributed representation: 考虑词之间的依赖关系
- word2vec(降维操作)
	- word embedding的一种distributed representation实现
	- 两种方式：Skip Gram和Common Bag of Words(CBOW)
	- CBOW
		- 输入词语，预测上下文
		- 输入为词语的one-hot编码向量，向量长度为V
		- 隐藏层包含N个神经元，只是对输入层做了加权和，没有激励函数(sigmoid/relu)，或者说激励函数是线性函数
		- 输出层也是长度为V的softmax向量
		- 输入为语句的话，分词，one-hot编码，通过隐藏层，然后求平均值
	- Skip Gram
		- 输入上下文，预测词语
		- 类似于CBOW逆向操作，输入目标presentation，输出context
		- 输出含义可以理解为该位置每个词语出现的概率
		- 反向传播算法求解参数(链式求导)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAwNDM2OTI1MV19
-->