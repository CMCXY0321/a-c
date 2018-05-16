- 完整的开发板有 CPU 和各种控制器（如 I2C 控制器、SPI 控制器、DMA 控制器等），CPU 和控制器可以统称为 SOC
- 除此之外还有各种外设 IP，如 LCD、HDMI、SD、CAMERA 等

#### 各级设备的展开
内核启动的时候是一层一层展开地去寻找设备，设备树之所以叫设备树也是因为设备在内核中的结构就像树一样，从根部一层一层的向外展开
大的圆圈中就是我们常说的 soc，里面包括 CPU 和各种控制器 A、B、I2C、SPI，soc 外面接了外设 E 和 F

- 展开 platform 设备
- 展开 i2c 设备
- 展开 spi 设备


#### 设备树信息
- reg 寄存器
  - 红色标注的代表着寄存器地址用几个数据量来表述，绿色标注的代表着寄存器空间大小用几个数据量来表述
- ranges 取值范围
  - ranges 代表了 local 地址向 parent 地址的转换，如果 ranges 为空的话代表着与 cpu 是 1:1 的映射关系，如果没有 range 的话表示不是内存区域