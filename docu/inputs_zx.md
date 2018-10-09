如何训练你自己的数据
____________________________

# 容易的方式
类似于train3.txt创建train/val，每一行包含图像的路径和ground truth路径。
ground truth 假定是一张图片。默认情况 下，红色是背景，紫色是前景。其它颜色是unknow，这些像素的LOSS被 忽略。
可以通过 hype来配置改变
```
  "data": {
    "road_color" : [255,0,255],
    "background_color" : [255,0,0]
  },
```

# 困难的方式
前边方法只适用于二类分割。可供选择的是写自己的输入生产和验证文件 。

在kitti_seg_input.py 实际数据是在函数_make_data_gen和_load_gt_file。如果修改这些地方可以 加载任何一种数据集。


验证文件 eval.py 是设计来使用 原始的验证代码。如果你训练自己的代码，最好自用自己的验证代码 。