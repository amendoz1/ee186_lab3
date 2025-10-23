# ee186_lab3
lab 3 submission

Written Responses:
1. Default address of accel = 0011001b (0x19 << 1)magnetometer =0011110b (0x1E<<1).
2. The sub-address tells the sensors which registers we are attempting to read from or write to. It’s used after writing to the device address; alone it wouldn’t do anything. The device address would help us choose which device on the i2c bus we wish to communicate with.
3. CTRL_REG1_A register is used to enable data collection from register 1.  The register address is 20h. We should write a non-zero value to bits ODR[3:0] to turn on the device and set some data rate and we should write 1s  to Zen, Yen and Xen bits to enable data collection along each axis. register would look something like ODR3 ODR2 ODR1 ODR0 LPen Zen Yen Xen -> [ODR[3:0] X 1 1 1]
4. To read x-axis data we would read from OUT_X_L_A (subaddress = 28h) and OUT_X_H_A (subaddress = 29h) where the latter contains the upper data bits which would be enabled by a higher resolution data mode. For y axis data we would read from OUT_Y_L_A (subaddress = 2Ah) and OUT_Y_H_A (subaddress = 2Bh) where the latter contains the upper data bits which contains the upper data bits if a higher resolution data mdoe is enabled. Finally to read the Z axis data we would read from OUT_Z_L_A (subaddress = 2Ch) and OUT_Z_H_A (subaddress = 2Dh), where the latter contains the upper data bits if a higher data resolution mode is enabled.
