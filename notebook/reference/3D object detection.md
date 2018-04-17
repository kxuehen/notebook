## 3D Bounding Box Estimation Using Deep Learning and Geometry

本文通过训练得出的目标2D检测框、尺寸、方向等信息，利用相机成像原理恢复目标的3D信息。

### 3D目标检测中相对方向、绝对方向和局部方向定义

![相对方向和绝对方向](files\1523959528400.png)

图中$\theta_l$是局部方向，其与车辆在图片中成像角度有关。$\theta$是全局方向，和世界坐标系有关。$\theta_{ray}$是相对方向，是车辆中心相对于拍摄相机的方向。这三者角度关系如下：
$$
\theta = \theta_l + \theta_{ray}
$$
