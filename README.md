自己实现l1-norm剪枝，网络结构vgg16和resnet56，数据集cifar10，使用原来的初始化权重初始化剪枝后的模型（彩票假说lottery ticket），而非随机初始化剪枝后的模型
```
l1-norm-pruning-lottery-ticket/
├── prun_resnet.py
├── prun_vgg.py
├── train_vgg.py
├── train_resnet.py
└── model/
    ├── resnet.py
    └── vgg.py
```
运行环境python=3.12, pytorch=2.7.0

训练vgg16
```
python train_vgg.py --save_dir logs
```
对vgg16进行剪枝
```
python prun_vgg.py --pretrain_path logs --save_dir logs
```
训练resnet56
```
python train_resnet.py --save_dir logs
```
对resnet56进行剪枝
```
python prun_resnet.py --pretrain_path logs --save_dir logs
```
实验结果：
| 模型 | 剪枝前accuracy | 剪枝后accuracy       |剪枝比例|
|------|----------|--------------|--|
|    vgg16  |      0.924    | 0.922             |    0.2 |       
|   resnet56   |      0.935    |0.931              |   0.2|         
