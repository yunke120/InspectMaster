# InspectMaster

## 通信协议说明

### 帧格式
|  字节  |   类型    |        可选值        | 说明 |
| :----: | :-------: | :------------------: | ---- |
| byte0  |   帧头    |         0xAA         |      |
| byte1  | 设备地址  |      0x01-0xFF       |      |
| byte2  | 命令类型  | 不同设备对应不同指令 |      |
| byte3  |   帧长    |   用户数据实际长度   |      |
| byte4  | 用户数据0 |                      |      |
| byte5  | 用户数据1 |                      |      |
| byte6  | 用户数据2 |                      |      |
| byte7  | 用户数据3 |                      |      |
| byte8  | 用户数据4 |                      |      |
| byte9  | 用户数据5 |                      |      |
| byte10 |  校验和   |  前10项和对255取余   |      |
| byte11 |   帧尾    |         0xDD         |      |

### 设备地址

| 地址 |   设备   |
| :--: | :------: |
| 0x01 |  机器人  |
| 0x02 | 吊舱云台 |
| 0x03 |  机械臂  |
| 0x04 |   电源   |
| 0x05 |   IMU    |
| 0x06 |  传感器  |

### 机器人(0x01) 

| 命令类型 |           用户数据            |    说明    |
| :------: | :---------------------------: | :--------: |
|   0x00   | 0x00,0x00,0x00,0x00,0x00,0x00 |    停止    |
|   0x01   | 0x00,0x00,0x00,0x00,0x00,0x00 |    前进    |
|   0x02   | 0x00,0x00,0x00,0x00,0x00,0x00 |    后退    |
|   0x03   | 0x00,0x00,0x00,0x00,0x00,0x00 |    右上    |
|   0x04   | 0x00,0x00,0x00,0x00,0x00,0x00 |    左上    |
|   0x05   | 0x00,0x00,0x00,0x00,0x00,0x00 |    右下    |
|   0x06   | 0x00,0x00,0x00,0x00,0x00,0x00 |    左下    |
|   0x07   | 0x00,0x00,0x00,0x00,0x00,0x00 |    右移    |
|   0x08   | 0x00,0x00,0x00,0x00,0x00,0x00 |    左移    |
|   0x09   | 0x00,0x00,0x00,0x00,0x00,0x00 | 原地右旋转 |
|   0x0A   | 0x00,0x00,0x00,0x00,0x00,0x00 | 原地左旋转 |
|          |                               |            |
|   0x20   |                               |  运行速度  |
|          |                               |            |
|   0xFF   | 0x00,0x00,0x00,0x00,0x00,0x00 |    握手    |
