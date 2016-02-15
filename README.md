# NodeMCU
NodeMCU is a Lua based firmware for Wi-Fi SoC ESP8266, ideal for IoT 
applications. The ESP8266 is a small, cheap (<3 EUR) Wi-Fi enabled micro 
controller featuring 802.11 b/g/n Wi-Fi, UART, I2C, SPI, GPIO an an 10 bit ADC. 

You can build a customized version of the firmware by yourself (e.g. using 
a Docker based builder) or you can build using an online build tool 
(http://nodemcu-build.com) which allows you to online configure and build
your firmare.

<img src="https://github.com/jandelgado/NodeMCU/blob/master/images/nodemcu_top.jpg" height="200"> <img src="https://github.com/jandelgado/NodeMCU/blob/master/images/nodemcu_bottom.jpg" height="200">

NodeMCU brings many interesting modules you can use out of the box in your
Lua scripts, e.g.:
  * csjon
  * gpio
  * http
  * mqtt
  * i2c
  * spi
  * ws2801 (Pixel LED)
  * ws2812 (Pixel LED)
  * u8g (LCD and OLED lib)
  * ... and many more

## Scripts 
### mqtt client
MQTT test client which connect to the test broker of test.mosquitto.org and 
subscribes to the temperature gauge test/random topic. Once connected 
and subscribed, the script will print out all changes published to the topic.

```
  m = mqtt.Client("testclient", 120)
  
  m:on("message", function(conn, topic, data)
    print(topic .. ":")
    if data ~= nil then
      print(data)
    end
  end)

  m:connect("test.mosquitto.org", 1883, 0, 0, function(conn) print("connected") end)
  m:subscribe("test/random", 0, function(conn) print("subscribe success") end)
```

## Links
  * https://en.wikipedia.org/wiki/ESP8266 
  * NodeMCU: http://nodemcu.com
  * NodeMCU Lua firmware: https://github.com/nodemcu/nodemcu-firmware and [API 
    documentation](http://nodemcu.readthedocs.org/en/dev/) 
  * Flashing tool: https://github.com/nodemcu/nodemcu-flasher
  * Custom firmware build service: http://nodemcu-build.com/

