---
layout: content
title: "Hardware"
---
The following products are required to run CallOnTV software.

|\#|Product Name|Price|Shopping Link|
|:----|:----|:----|:----|
|1|Raspberry Pi 4Bwith at least 4GB of RAM(Amazon links includes the whole bundle i.e. Raspberry PI Power adapter, Samsung microSDXC card, Fan, Case, microHDMI to HDMI cable, microSDXC Reader)|~150$|[Amazon USA](https://www.amazon.com/dp/B08B6G2RFG/)[Amazon Canada](https://www.amazon.ca/dp/B09Q4TQBSZ/)[Digikala](https://www.digikala.com/product/dkp-2023121/)|
|2|32G+ SanDisk Extreme MicroSDXCor32G+ Samsung Evo+ MicroSD card|~8$|[Digikala](https://www.digikala.com/search/category-memory-cards/sandisk/?types[0]=6522&attributes[3877][0]=24597) Sandisk[Digikala](https://www.digikala.com/search/category-memory-cards/samsung/?types[0]=6522&attributes[3877][0]=24597) Samsung|
|3|Raspberry Pi 15W USB-C Power Supply|~20$|[Bir-Robotic](https://www.digikala.com/product/dkp-6543154)|
|4|K-Net Plus Micro HDMI to HDMI 2.0 cable|~8$|[Digikala](https://www.digikala.com/product/dkp-795389/)|
|5|Raspberry 4 Case|~4$|[Digikala](https://www.digikala.com/product/dkp-2158556/)|
|6|Logitech BRIO webcam|~180$|[Amazon USA](https://www.amazon.com/dp/B01N5UOYC4)[Amazon Canada](https://www.amazon.ca/dp/B01N5UOYC4)[Digikala](https://www.digikala.com/product/dkp-2450826/)|
|7|Heat Sink for Raspberry Pi 4|3$|[Bir-Robotic](https://bir-robotic.ir/product/%d9%87%db%8c%d8%aa-%d8%b3%db%8c%d9%86%da%a9-%d8%a8%d8%b3%d8%aa%d9%87-3-%d8%b9%d8%af%d8%af%db%8c-%d9%85%d9%86%d8%a7%d8%b3%d8%a8-%d8%b1%d8%b2%d8%a8%d8%b1%db%8c-%d9%be%d8%a7%db%8c-4/)|
|8|Brushless 8cm x 8cm fan for Pi|8$|[Digikala](https://www.digikala.com/product/dkp-4989587/)|
| |Total|~420$| |

In addition, your TV must support HDMI-CEC so that the raspberrypi can Power On/Off and switch your TV to HDMI. A list of supported TV brands can be checked at [libCEC](http://libcec.pulse-eight.com/Vendor/Support) website.

We STRONGLY recommend Logitech BRIO webcam that has both a 90° field of view and a clear powerful microphone. Other cheaper logitech webcams such as C930E, C925, C920, C310, C270, … have serious problems such as narrow field of view and unclear microphone and are not recommended at all.

The following table shows the result for TVs we have tested for HDMI-CEC. You can check the User Manual of your TV and search for CEC keyword in it to see if HDMI-CEC is supported. HDMI-CEC is usually not supported if there is no CEC keyword in the manual of your product or in the specification page of the product on manufacturer’s website.


|TV Brand|Model|HDMI-CEC support|
|:----|:----|:----|
|Daewoo|DLE-49H1800U|[Not Supported](https://daewoo.ir/product_cat/av/dle-49h1800u/) ❌|
|Sony|KD-49X8300C|[Supported](https://www.sony.com.sg/electronics/support/televisions-projectors-lcd-tvs-android-/kd-49x8300c/specifications) ✅|
|Samsung|UA-40D5950RM|[Supported](https://www.samsung.com/iran/support/model/UA40D5500RMSHD/#downloads) ✅|
|Samsung|UA-49K5890AWCHD|[Not Supported](https://www.samsung.com/iran/support/model/UA49K5100AWCHD/#downloads) ❌|
|Samsung|UA-46F6450AMSHD|[Supported](https://www.samsung.com/levant/support/model/UA46F6400ARSOT/) ✅|
|Samsung|UA-55KU7970|[Supported](https://www.samsung.com/iran/tvs/uhd-4k-tv/ku7000-55-inch-crystal-uhd-smart-tv-ua55ku7000wshd/) ✅|
|LG|43LK5730PVC|[Supported](https://www.lg.com/africa/tvs/lg-43LK5730PVC) ✅|

## Display resolution

CallOnTV utilizes Google Meet to establish video calls. The screen resolution requirement is the same as [Google meet requirements](https://support.google.com/a/answer/4541234) and must be at least 1280 x 720 pixels. 

For best video quality, we recommend 1920 x 1080 pixels.

Screen resolution can be set from Raspberry Pi Menu -> Preferences -> Screen Configuration -> Right click on your display and set the resolution.

### Power Usage

We have measured the power usage of our product by using a [USB-C cable with display power](https://www.mcdodo.com.ph/products/ca-869-digital-pro-type-c-5a-data-cable-1-2m). The power usage is about 4W when in idle mode and about 11W when on a call using CallOnTV

|![Idle](/assets/img/power-usage-0.png)|![In-use](/assets/img/power-usage-1.png)|
|:--:| 
|*Power usage of CallOnTV in idle mode* | *Power usage of CallOnTV on a video call*|

### Bandwidth Usage

The bandwidth usage of streaming depends on the quality of video calls which is automatically chosen by Google Meet. The bandwidth requirement of Google meet is available [here](https://support.google.com/a/answer/4541234).

#### HD video quality bandwidth requirements
Latency should be less than 50 ms when pinging Google's public DNS server at 8.8.8.8. 
Outbound signals from a participant in all situations must meet a 3.2 mbps bandwidth requirement. 
For 2 participants, the bandwidth requirement is 2.6mbps for HD video quality and 1mbps for SD video quality.