# GPIOViewer Arduino Library to see live GPIO Pins on ESP32 boards

**Transforms the way you troubleshoot your microcontroller projects**.

### Youtube Tutorial
https://youtu.be/UxkOosaNohU

### Installation

- Downnload the code and install the library in the Arduino IDE : `Sketch > Include Library > Add ZIP Library...`
- Install the [ESPAsyncWebServer](https://github.com/me-no-dev/ESPAsyncWebServer) library in the same way `Sketch > Include Library > Add ZIP Library...`
- Install the the [AsyncTCP](https://github.com/dvarrel/AsyncTCP) using the Arduino IDE Library Manager.

### Usage
>ℹ️ You can also use get examples provided with the library in the Arduino IDE through the menu `File > Examples > GPIOViewer`<br>
>ℹ️ You only need to include the library, declare the GPIOViewer and call begin() at the end of your setup, and that's it!<br>
>ℹ️ The URL to the web GPIO viewer application is printed on the serial monitor<br>
```c
#include <gpio_viewer.h> // Must me the first include in your project
GPIOViewer gpio_viewer;

void setup()
{
  Serial.begin(115200);

  // Comment the next line, If your code aleady include connection to Wifi
  gpio_viewer.connectToWifi("Your SSID network", "Your WiFi Password");
  // gpio_viewer.setPort(5555);   // You can set the http port, if not set default port is 8080

  // Your own setup code start here

  // Must be at the end of your setup
  // gpio_viewer.setSamplingInterval(25); // You can set the sampling interval in ms, if not set default is 100ms
  gpio_viewer.begin();
}
```
>ℹ️ The default HTTP port is **8080** and default sampling interval is **100ms**.


### Library Size

- The GPIOViewer Library adds 50 KB to your projects.
- No worries!  All the assets (ex. board images) of the web application are loaded from github pages and don't add to the size of your projects.

### GPIO Supported

- Digital
- PWM

### Performance
- Ensure you have a strong Wifi signal with a good transfer rate.  25ms sampling interval works great on Wifi 6 with 125 Mbps.
- If you get "ERROR: Too many messages queued" on the Serial Monitor, this means the data is not read fast enough by the web application.  The data will still be displayed, but with some latency.  Reduce the sampling interval or try to improve your Wifi performance.

### ESP32 Boards Supported
>ℹ️ You can use the "Generic View" in the GPIO Web Application to see GPIO pin activites live even if your board image is not listed <br>
>ℹ️ You can also request an ESP32 board image addition by [creating a new issue](https://github.com/thelastoutpostworkshop/gpio_viewer/issues).


| Description        | Image                               | Pinout                               |
|--------------------|-------------------------------------|-------------------------------------|
| ESP32 WROOM 32D (38 pins)  | ! <img src="https://github.com/thelastoutpostworkshop/microcontroller_devkit/blob/main/gpio_viewer/assets/devboards_images/ESP32-VROOM-32D.png" width="100">             | <img src="https://docs.espressif.com/projects/esp-idf/en/latest/esp32/_images/esp32-devkitC-v4-pinout.png" width="100">|
| ESP32 WROOM 32D (30 pins)   | ! <img src="https://github.com/thelastoutpostworkshop/microcontroller_devkit/blob/main/gpio_viewer/assets/devboards_images/ESP32-VROOM-32D-30pins.png" width="100">             |<img src="https://raw.githubusercontent.com/AchimPieters/esp32-homekit-camera/master/Images/ESP32-30PIN-DEVBOARD.png" width="100">|
| ESP32 D1 R32  | ! <img src="https://github.com/thelastoutpostworkshop/microcontroller_devkit/blob/main/gpio_viewer/assets/devboards_images/ESP32_D1_R32.png" width="100">             |<img src="https://ito-iot.jp/sbc/WeMosD1R32-pinout.png" width="100">  |
| ESP32 C3 Wroom-02  | ! <img src="https://github.com/thelastoutpostworkshop/microcontroller_devkit/blob/main/gpio_viewer/assets/devboards_images/esp32-C3-Wroom-02.png" width="100">             |<img src="https://m.media-amazon.com/images/S/aplus-media-library-service-media/a80e998c-f2b4-4c4a-9ee7-d97ede61e14c.__CR0,0,970,600_PT0_SX970_V1___.jpg" width="100">|
| ESP32 Wroom-32UE  | ! <img src="https://github.com/thelastoutpostworkshop/microcontroller_devkit/blob/main/gpio_viewer/assets/devboards_images/esp32-Wroom-32UE.png" width="100">             |<img src="https://media.springernature.com/lw685/springer-static/image/chp%3A10.1007%2F978-3-031-02447-4_74/MediaObjects/519315_1_En_74_Fig2_HTML.png" width="100">|
| ESP32 S3 Wroom-1  | ! <img src="https://github.com/thelastoutpostworkshop/microcontroller_devkit/blob/main/gpio_viewer/assets/devboards_images/esp32-s3-wroom-1.png" width="100">             |<img src="https://docs.espressif.com/projects/esp-idf/en/latest/esp32s3/_images/ESP32-S3_DevKitC-1_pinlayout_v1.1.jpg" width="100">|
| Esp32 S2 Mini V1.0.0  | ! <img src="https://github.com/thelastoutpostworkshop/microcontroller_devkit/blob/main/gpio_viewer/assets/devboards_images/Esp32 S2 Mini V1.0.0.png" width="100">             |<img src="https://www.studiopieters.nl/wp-content/uploads/2022/08/WEMOS-ESP32-S2-MINI.png" width="100">|
| ESP32-POE  | ! <img src="https://github.com/thelastoutpostworkshop/microcontroller_devkit/blob/main/gpio_viewer/assets/devboards_images/ESP32-POE.png" width="100">             |<img src="https://www.olimex.com/Products/IoT/ESP32/ESP32-POE/resources/ESP32-POE-GPIO.png" width="100">|
| ESP32-C3-Mini  | ! <img src="https://github.com/thelastoutpostworkshop/microcontroller_devkit/blob/main/gpio_viewer/assets/devboards_images/ESP32-C3-Mini.png" width="100">             |<img src="https://www.wemos.cc/en/latest/_static/boards/c3_mini_v2.1.0_4_16x9.png" width="100">|
