# NAME CHANGE IN LIBRARAY MANAGER - PLEASE READ
Hi all DIY gaming enthusiasts.
Please be aware that the official name for this library in the library manager has changed from
	
	ESP32 BLE Gamepad  -->  ESP32-BLE-Gamepad

This is to make it consistent with those who were also downloading it from GitHub and had 2 versions with different names and was leading to confusion.
The library manager was automatically renaming the folder ESP32_BLE_Gamepad upon installation bue to the spaces in the name. The library with the old name has been de-listed from the manager and only the new one remains.
Please remove/delete the old version by deleting the ESP32_BLE_Gamepad folder within your libraries folder.

Apologies for the early adopters, but it will save a lot of confusion moving forward.

# 请阅读-库名变更
大家好，所有DIY游戏发烧友。
请注意，库管理器中该库的正式名称已从

      ESP32 BLE Gamepad  -->  ESP32-BLE-Gamepad

这是为了使其与那些也从GitHub下载并具有两个名称不同的版本的人保持一致，并导致混乱。
安装时，库管理器会根据名称中的空格自动重命名文件夹ESP32_BLE_Gamepad。 具有旧名称的库已从管理器中除名，仅保留了新库。
请通过删除库文件夹中的ESP32_BLE_Gamepad文件夹来删除/删除旧版本。

为早期采用者道歉，但它将避免前进过程中的许多混乱。

# ESP32-BLE-Gamepad
Bluetooth LE Gamepad library for the ESP32

This library allows you to make the ESP32 act as a Bluetooth Gamepad and control what it does. E.g. move axes and press buttons

Due to popular demand, it supports a large array of buttons and axes. You only need to wire up the amount you'd like to use in your project. If you need more GPIO on your ESP32, you should search "Arduino GPIO expander". The i2c bus (uses just 2 GPIO pins) can be used to add multiple GPIO expanders to add all the GPIO you would ever need. 

# ESP32蓝牙游戏手柄
ESP32的蓝牙LE游戏手柄库

该库可让您使ESP32充当Bluetooth Gamepad并控制其功能。 例如。 移动轴并按下按钮

由于受欢迎的需求，它支持各种各样的按钮和轴。 您只需要连接您想在项目中使用的数量即可。 如果您需要在ESP32上使用更多GPIO，则应搜索“ Arduino GPIO扩展器”。 i2c总线（仅使用2个GPIO引脚）可用于添加多个GPIO扩展器，以添加您所需的所有GPIO。

## Features

 - [x] Button press (64 buttons)
 - [x] Button release (64 buttons)
 - [x] Axes movement (6 axes (16 bit) (x, y, z, rZ, rX, rY) --> (Left Thumb X, Left Thumb Y, Right Thumb X, Right Thumb Y, Left Trigger, Right Trigger))
 - [x] 2 Sliders (16 bit) (Slider 1 and Slider 2)
 - [x] 4 point of view hats (ie. d-pad plus 3 other hat switches)
 - [x] Report optional battery level to host (basically works, but it doesn't show up in Android's status bar)
 - [x] Customize Bluetooth device name/manufacturer
 - [x] Compatible with Windows
 - [x] Compatible with Android (Android OS maps default buttons / axes / hats slightly differently than Windows)
 - [x] Compatible with Linux
 - [x] Compatible with MacOS X
 - [ ] Compatible with iOS (No - not even for accessibility switch - This is not a “Made for iPhone” (MFI) compatible device)

## 特征
 - [x] 按下按钮（64个按钮）
 - [x]  释放按钮（64个按钮）
 - [x]  轴移动（6轴（16位）（x，y，z，rZ，rX，rY）->（左手拇指X，左手拇指Y，右手拇指X，右手拇指Y，左触发器，右触发器））
 - [x]  2个滑块（16位）（滑块1和滑块2）
 - [x]  4个视角帽子（即d-pad和3个其他帽子开关）
 - [x]  向主机报告可选的电池电量（基本可用，但不会显示在Android状态栏中）
 - [x]  自定义蓝牙设备名称/制造商
 - [x]  与Windows兼容
 - [x]  与Android兼容（Android OS映射的默认按钮/轴/帽子与Windows稍有不同）
 - [x]  与Linux兼容
 - [x]  与MacOS X兼容
 - [ ]  与iOS兼容（否-甚至没有辅助功能开关-这不是“ Made for iPhone”（MFI）兼容设备）

## Installation
- (Make sure you can use the ESP32 with the Arduino IDE. [Instructions can be found here.](https://github.com/espressif/arduino-esp32#installation-instructions))
- [Download the latest release of this library from the release page.](https://github.com/lemmingDev/ESP32-BLE-Gamepad/releases)
- In the Arduino IDE go to "Sketch" -> "Include Library" -> "Add .ZIP Library..." and select the file you just downloaded.
- You can now go to "File" -> "Examples" -> "ESP32 BLE Gamepad" and select the example to get started.

## 安装
- （确保您可以将ESP32与Arduino IDE配合使用。[说明可以在这里找到。]（https://github.com/espressif/arduino-esp32#installation-instructions））
- [从发布页面下载此库的最新版本。]（https://github.com/lemmingDev/ESP32-BLE-Gamepad/releases）
- 在Arduino IDE中，转到“素描”->“包含库”->“添加.ZIP库...”，然后选择刚下载的文件。
- 现在您可以转到“文件”->“示例”->“ ESP32 BLE游戏手柄”，然后选择示例以开始使用。

## Example

``` C++
/*
 * This example turns the ESP32 into a Bluetooth LE gamepad that presses buttons and moves axis
 * 
 * Possible buttons are:
 * BUTTON_1 through to BUTTON_64 
 * 
 * Possible DPAD/HAT switch position values are: 
 * DPAD_CENTERED, DPAD_UP, DPAD_UP_RIGHT, DPAD_RIGHT, DPAD_DOWN_RIGHT, DPAD_DOWN, DPAD_DOWN_LEFT, DPAD_LEFT, DPAD_UP_LEFT
 * (or HAT_CENTERED, HAT_UP etc)
 *
 * bleGamepad.setAxes takes the following int16_t parameters for the Left/Right Thumb X/Y, uint16_t for the Left/Right Triggers plus slider1 and slider2, and hat switch position as above: 
 * (Left Thumb X, Left Thumb Y, Right Thumb X, Right Thumb Y, Left Trigger, Right Trigger, Hat switch positions (hat1, hat2, hat3, hat4));
 */
 
#include <BleGamepad.h> 

BleGamepad bleGamepad;

void setup() 
{
  Serial.begin(115200);
  Serial.println("Starting BLE work!");
  bleGamepad.begin();
}

void loop() 
{
  if(bleGamepad.isConnected()) 
  {
    Serial.println("Press buttons 5 and 32. Move all axes to max. Set DPAD (hat 1) to down right.");
    bleGamepad.press(BUTTON_5);
    bleGamepad.press(BUTTON_32);
    bleGamepad.setAxes(32767, 32767, 32767, 32767, 65535, 65535, 65535, 65535, DPAD_DOWN_RIGHT); //(can also optionally set hat2/3/4 after DPAD/hat1 as seen below)
    // All axes, sliders, hats can also be set independently. See the IndividualAxes.ino example
	delay(500);

    Serial.println("Release button 5. Move all axes to min. Set DPAD (hat 1) to centred.");
    bleGamepad.release(BUTTON_5);
    bleGamepad.setAxes(-32767, -32767, -32767, -32767, 0, 0, 0, 0, DPAD_CENTERED, HAT_CENTERED, HAT_CENTERED, HAT_CENTERED);
    delay(500);
  }
}
```
By default, reports are sent on every button press/release or axis/slider/hat movement, however this can be disabled, and then you manually call sendReport on the gamepad instance as shown in the IndividualAxes.ino example.

There is also Bluetooth specific information that you can use (optional):

Instead of `BleGamepad bleGamepad;` you can do `BleGamepad bleGamepad("Bluetooth Device Name", "Bluetooth Device Manufacturer", 100);`.
The third parameter is the initial battery level of your device. To adjust the battery level later on you can simply call e.g.  `bleGamepad.setBatteryLevel(50)` (set battery level to 50%).
By default the battery level will be set to 100%, the device name will be `ESP32 BLE Gamepad` and the manufacturer will be `Espressif`.


## Credits
Credits to [T-vK](https://github.com/T-vK) as this library is based on his ESP32-BLE-Mouse library (https://github.com/T-vK/ESP32-BLE-Mouse) that he provided.

Credits to [chegewara](https://github.com/chegewara) as the ESP32-BLE-Mouse library is based on [this piece of code](https://github.com/nkolban/esp32-snippets/issues/230#issuecomment-473135679) that he provided.

## 归功于
归功于[T-vK]（https://github.com/T-vK），因为此库基于他的ESP32-BLE-Mouse库（https://github.com/T-vK/ESP32-BLE- 他提供的鼠标）。

由于[ESP32-BLE-Mouse]库基于[这段代码]（https://github.com/nkolban/esp32-snippets/issues/ 230＃issuecomment-473135679）。

## Notes
Use [this](http://www.planetpointy.co.uk/joystick-test-application/) Windows test app to test/see all of the buttons

You might also be interested in:
- [ESP32-BLE-Mouse](https://github.com/T-vK/ESP32-BLE-Mouse)
- [ESP32-BLE-Keyboard](https://github.com/T-vK/ESP32-BLE-Keyboard)

## 注意
使用[this]（http://www.planetpointy.co.uk/joystick-test-application/）Windows测试应用程序来测试/查看所有按钮

你也可能对此有兴趣：
-[ESP32-BLE-Mouse]（https://github.com/T-vK/ESP32-BLE-Mouse）
-[ESP32-BLE-Keyboard]（https://github.com/T-vK/ESP32-BLE-Keyboard）
