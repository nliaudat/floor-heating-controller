# floor-heating-controller
esphome firmware for [esp32_8ch_motor_shield](https://github.com/nliaudat/esp32_8ch_motor_shield/)


#install esphome
```
pip install --upgrade esphome
```

#Preparation
* Check the [wiki](https://github.com/nliaudat/floor-heating-controller/wiki)
* Adapt config.yaml to your needs
* Adapt sensor_temperature.yaml with your temperature sensors
* Adapt wifi.yaml + secrets.yaml

#1st time upload : 
* Detach the ESP32 board from the shield and connect it the through usb
* for flashing : press boot button for 2-3 seconds before the serial connection initialize
* After OTA update, the EN (reset) button must be pressed to run firmware
* do not use gpio12 (MTDI)
* the future binary upload will go trough OTA wireless

#compile to check for errors
```
esphome compile config.yaml
```

#compile & upload
```
esphome run config.yaml
```
