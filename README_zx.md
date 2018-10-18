# 0 介绍
小数据集上。训练仅用了250张标注图片。MaxF1达到96%。Inference仅95ms每张图片。
与TensorVision后端兼容。
KittiBox -->> detection
MultiNet -->> segmentation, classification and detection


# 1 安装依赖
```
pip install numpy scipy pillow matplotlib commentjson
```
或者
```
pip install -r requirements.txt
```

# 2 安装
## 2.1 克隆仓库
```
git clone https://github.com/MarvinTeichmann/KittiSeg.git
```

## 2.2 初始化子模块
```
git submodule update --init --recursive
```
## 2.3 下载道路数据
### 2.3.1 手动下载
```
wget http://www.cvlibs.net/download.php?file=data_road.zip
```
### 2.3.2 自动下载
```
python download_data.py --kitti_url URL_YOU_RETRIEVED
```
vgg16.npy 下载存储到 DATA/weights
data_road.zip 下载解压到 DATA/data_road
data/train3.txt data/val3.txt data/testing.txt 复制到 DATA/data_road


## 2.4 注意
只运行demo.py的话不需要下载道路数据。2.3仅是你用train.py训练自己的模型时才必要。推荐使用2.3.2下载数据，这会自动提取和准备数据。如果你想掌握数据存储在哪，请看3.2Manage data storage。


# 3 教程
## 3.1 入门
```
# ubuntu : it can run with python3.6
python demo.py --input_image data/demo/demo.png
python evaluate.py
python train.py --hypes hypes/KittiSeg.json
```

### 3.1.1 demo.py
logdir=RUNS/KittiSeg_pretrained

如果你想理解代码，建议先看demo.py。作者已经在每一步写了说明。

## 3.2 数据存储管理
默认数据存储在 KittiSeg/DATA下，
运行的输出存储在 KittiSeg/RUNS 。
可以来通过修改$TV_DIR_DATA 和 $TV_DIR_RUNS改变存储路径。

## 3.3 RUNDIR 和 实验组织

为了记录所有实验，可以 用--flag给每个rundir一个唯一的名称
--project运行单独的目录来运行不同的实验。
```
python train.py \
    --project batch_size_bench \
    --name size_5
# $TV_DIR_RUNS/KittiSeg/batch_size_bench/size_5_KittiSeg_2017_02_08_13.12
```

## 3.4 修改模型 和 训练自己的数据
hypes/KittiSeg.json 控制模型。


# 4 利用 TensorVision 后端


# 5 有用的标志和变量




