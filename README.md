## Siamese：孪生神经网络在Pytorch当中的实现
---
參考連結 : https://github.com/bubbliiiing/Siamese-pytorch    

## 预测步骤
### a、使用预训练权重
1. 下载完库后解压，在百度网盘下载Omniglot_vgg.pth，放入model_data，运行predict.py，依次输入    
```python
img/Angelic_01.png
```
```python
img/Angelic_02.png
```  
### b、使用自己训练的权重
1. 按照训练步骤训练。  
2. 在siamese.py文件里面，在如下部分修改model_path使其对应训练好的文件；**model_path对应logs文件夹下面的权值文件**。    
```python
_defaults = {
    "model_path": 'model_data/Omniglot_vgg.pth',
    "input_shape" : (105, 105, 3),
}
```
3. 运行predict.py，输入   
```python
img/Angelic_01.png
```
```python
img/Angelic_02.png
```

## 训练步骤
可参考我的CSDN博客https://blog.csdn.net/weixin_44791964/article/details/107343394
### a、训练Omniglot例子  
Omniglot数据集中数据存放格式有三级：
```python
- image_background
	- Alphabet_of_the_Magi
		- character01
			- 0709_01.png
			- 0709_02.png
			- ……
		- character02
		- character03
		- ……
	- Anglo-Saxon_Futhorc
	- ……
```
训练步骤为：  
1. 下载数据集，放在根目录下的dataset文件夹下。     
2. 运行train.py开始训练。   
### b、训练自己相似性比较的模型
如果大家想要训练自己的数据集，可以将数据集按照如下格式进行摆放。    
```python
- image_background
	- character01
		- 0709_01.png
		- 0709_02.png
		- ……
	- character02
	- character03
	- ……
```
相比Omniglot少了一级。每一个chapter里面放同类型的图片。    
训练步骤为：  
1. 按上述格式放置数据集，放在根目录下的dataset文件夹下。     
2. 之后将train.py当中的train_own_data设置成True。  
3. 运行train.py开始训练。 

### Reference
https://github.com/tensorfreitas/Siamese-Networks-for-One-Shot-Learning
