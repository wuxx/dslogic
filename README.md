## DSLogic hack
#### 拆机说明  
https://www.bilibili.com/video/av83163258/  
#### DSView使用介绍  
https://www.bilibili.com/video/av83163888/
#### 手动将DSLogic Basic版本升级成Plus版本
https://www.bilibili.com/video/av84030696/  
1. 自行购买SDRAM（我使用的型号为MT48LC16M16A2P-6A）  
2. 将DSLogic PCB上的EEPROM用热风枪吹下来
3. 使用编程器读出EEPROM（可使用实验室推出的开源编程器，也可使用市面上常见的CH341、XTW100等编程器）
4. 修改读出的镜像，修改点参考Makefile
5. 将修改好的镜像使用编程器重新刷入EEPROM中（稳妥起见，建议先对原来读出的镜像做一个备份）
6. 将EEPROM重新焊接回PCB上，焊接上SDRAM。
7. DSLogic重新上电，检查是否升级成功