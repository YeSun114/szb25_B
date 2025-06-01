# 模型介绍

## 第一问
想要把按照bt2020标准录制的视频放到普通显示器上播放,那么需要进行色与转换,$X_{srgb}=M*X_{bt2020}$,为了最小化$delta E$,我们需要找到一个合适的M,
其中$delta E$是CIELab色与空间所规定的视觉颜色偏差.所需的已知条件有bt2020三原色波长,常用显示器rbg波长,另外两色域空间下白点均取"D65"

使用python的colour-science库来完成

- 从RGB_COLOURSPACES['ITU-R BT.2020']中抽取1000个点,

- $X_{srgb}=M* X_{bt2020}$进行转换,转换的约束条件为转换后的色彩必须属于srgb色域空间

- 利用RGB_to_XYZ, XYZ_to_Lab, 将两空间的rgb向量逐步转换成cielab标准表示的色彩向量,然后计算delta_E,

- 优化M使得各个采样点delta_E均值最小化




 
