## VOC转YOLO格式与YOLO转VOC格式

### 使用方法:

- 在配置文件中 `config.py` 根据数据集修改变量
- 运行 `python main.py --yolo2voc`执行**YOLO**到**VOC**
- 运行 `python main.py --voc2yolo`执行**VOC**到**YOLO**
- 运行 `python main.py --voc2yolo_a`执行**VOC**到**YOLO** (绝对坐标值)

### Pascal VOC转换到YOLO

`python main.py --voc2yolo`

- `<object-class>` - 整数数字 `0`到`(classes-1)`
- `<x> <y> <width> <height>` - `float` 相对于宽高的占比数值，范围在 `(0.0, 1.0]`
- 例如: 宽：`<x> = <absolute_x> / <image_width>，高：<height> = <absolute_height> / <image_height>`
- 注意: `<x> <y>` - 是方格的中心点 (不是左上角点)

<div align="center">
    <p><code>zidane.jpg</code></p>
    <img src="assets/zidane.jpg" height="400px" alt="downloaded from ultralytics">
</div>

上图中的标签包括两个人(类别 0)和一个领带(类别 27):

`<object-class> <x> <y> <width> <height>`
<div align="center">
    <img src="assets/zidane_txt.jpg", height="200px" alt="downloaded from ultralytics">
</div>

### Pascal VOC转换到YOLO绝对坐标

`python main.py --voc2yolo_a`

- `<object-class>` - 整数数字 `0`到`(classes-1)`
- `<x_min> <y_min> <x_max> <y_max>` - `int` 对象坐标的绝对值
- 例如: `<object-class> <x_min> <y_min> <x_max> <y_max>`:

```
1 255 247 425 468
0 470 105 680 468
1 152 356 658 754
```

### 参考

1. https://github.com/AlexeyAB/Yolo_mark/issues/60
2. https://github.com/jahongir7174/YOLO2VOC
3. https://github.com/yakhyo/yolo2voc
