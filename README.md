1.文件和文件夹介绍
	midi_train(文件夹): 用来训练模型的midi训练集
	生成的音乐(文件夹): 使用模型生成的音乐demo
	autoencoder.py(文件): 主要模型代码
	mid.py、mid2.py(文件): 测试其他模型时瞎写的(不用看)


2.问题分析
该问题需要我们训练网上下载的midi音乐旋律，建立自己的模型，让该模型能够自动的生成优美的旋律。这个问题比较特殊，一般的机器学习模型都有评判的依据，该依据与模型生成的结果产生loss，然后修正参数从而得到模型。而该任务却没有评判的依据，生成的音乐并不知道好还是不好。因此我们巧妙的将数据集本身做为评判的依据，我们认为数据集本身就是最好的音乐，因此我们生成的音乐和数据集本身音乐做比较就ok了。因此我们使用了autoencoder自编码网络取得了较好的效果，首先将输入的midi音乐转换为[-1,4]的矩阵，-1代表着任意。然后让其做为自编码网络的输入，自编码网络的输出和自己本身做比较，得到loss反向梯度下降进行训练。分别让模型训练128、256、512、1024次得到了生成的音乐。 发现生成的音乐还是不错的，保持着部分训练集的旋律，能明显的听出有节奏的midi旋律。后来尝试着使用GAN网络进行训练，由于参数调整不足，生成的旋律并不乐观，这里就没给出具体的GAN网络模型。

