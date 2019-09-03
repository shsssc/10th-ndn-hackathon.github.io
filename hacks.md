---
layout: page
title: Hacks Proposals
---

{::options toc_levels="2,3" /}

* TOC
{:toc}


## 1. ESP32 Video Doorbell

### **[Pitch Slides]({% asset 1-doorbell-junxiao.pdf @path %})**

**Project Lead:**
- Junxiao Shi

<!-- Project Members: TBD -->
**Prefered Team Size:**
- 2

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- Develop a video doorbell using two ESP32 modules programmed with Arduino environment. This would be a fun hands-on exercise for a new developer.

**Briefly describe the tasks**
1. Develop the display unit on an ODROID-GO handheld console.
Upon receiving and verifying a signed Interest, it plays a ringtone, and displays images retrieved from the camera unit.

2. Develop the camera unit on an AI Thinker ESP32-CAM module.
When a hardware button is pressed, it sends a signed Interest to the display unit to sound ringtone.
Upon receiving an Interest for image, it captures an image from the OV2640 camera and sends it as Data segments.

3. NDN library: https://github.com/yoursunny/esp8266ndn/
Camera library: https://github.com/yoursunny/esp32cam/

**Any specific tools or language**
- Project author will loan 1x ODROID-GO, 1x ESP32-CAM, 1x USB-UART, 1x button.
- Each task needs 1 participant who can write C++.

**Expected outcomes**
- Finish all tasks.

## 2. NFD on OpenWrt Home Router

### **[Pitch Slides]({% asset 2-openwrt-junxiao.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Prefered Team Size:**
- 3

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- OpenWrt is an embedded operating system designed for home routers.
  @yoursunny has ported ndn-cxx, NFD, and ndn-tools as OpenWrt packages, and tested their basic functionality.
  Configuration is integrated to UCI (Unified Configuration Interface), and dynamically converted to nfd.conf and scripts.
  Currently, the user can only interact with these program via command line and config files.
- This project is to integrate NFD and ndn-tools into LuCI, OpenWrt's web user interface.
  Then, it would be easier to deploy and use NDN on home routers.


**Briefly describe the tasks**
- Develop LuCI pages to:
1. display NFD global counters, face counters, and RIB routes, with AJAX-based updates.
2. create faces and insert routes, one-time via `nfdc` command or permanently via UCI.
3. edit strategy choices via UCI.
4. run diagnostic tests via `ndnping` command.

- (optional)
Investigate how to lockdown NFD management: only authorized applications may send commands to NFD face, strategy-choice, and RIB management.
@yoursunny has attempted this but NFD is crashing, so this requires debugging.

- (optional)
Port server components of Xinyu's NDN Control Center (ndn-cc) as an OpenWrt package.
Future development of LuCI pages would be able to reuse ndn-cc's REST API.

**Any specific tools or language**
- Lua programming language: it's easy to learn during the hackathon.
- Linux userspace environment (physical, virtual, or WSL), at least 20GB disk space to install OpenWrt buildroot.
- Wired Ethernet port on the laptop.
- Project author will loan 2x Banana Pi R2 home routers, with pre-installed OpenWrt 18.06.2 and NDN packages.

**Expected outcomes**
- Display the LuCI pages mentioned above.

## 3. NDNCERT Client, Certificate Bundle, and Prefix Announcement in ndn-js and esp8266ndn

### **[Pitch Slides]({% asset 3-testbed-junxiao.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Prefered Team Size:**
- 5

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- [NDN certificate management protocol (NDNCERT)](https://github.com/named-data/ndncert/wiki/NDNCERT-Protocol-0.2) enables certificate application and issuance in NDN. NDNCERT protocol has been verified by NIST Computer Security Division, and is being implemented by Zhiyi Zhang at UCLA. NDNCERT certificate authority will replace ndncert legacy website for NDN testbed certificate issuance.
- [Certificate bundle](https://redmine.named-data.net/issues/2766#note-30) is a way to collect multiple certificates necessary to validate a packet into a single segmented object, in order to enable more efficient validation. Specification of certificate bundle has been approved at NFD call in May 2019, and is being implemented by Jeremy Clark at Memphis. In the future, prefix registration on the NDN testbed may allow the end host to supply a certificate bundle, so that the validator does not need to retrieve certificates from every CA, which in turn depends on every CA being online.
- The [prefix announcement object](https://redmine.named-data.net/projects/nfd/wiki/PrefixAnnouncement) is a Data packet that represents an application's intent of registering a prefix toward itself. Prefix announcement object is already used in NFD's self-learning implementation. Next version of NFD Management protocol will also allow using a prefix announcement object in place of a Name along with other flags.  This project is to integrate NDNCERT client, certificate bundle publisher, and prefix announcement encoding/decoding functionality into ndn-js and esp8266ndn libraries. This prepares web applications and ESP32 devices to work with next generation of prefix registration procedure on the NDN testbed.

**Briefly describe the tasks**

Notice: scope of this project is flexible, every task is optional, one or two tasks per person.

- Develop the following features in ndn-js:
	- 1. NDNCERT client with PIN challenge.
	- 2. Certificate bundle publisher.
	- 3. PrefixAnnouncement encoding/decoding.

They should be written in TypeScript or ES2019, use a Promise-style API, and tested with Node 12.
Do not write in outdated ES5: browser and older Node can be supported via transpilers and polyfills.

- Develop the following features in esp8266ndn:
	- 4. NDNCERT client with PIN challenge.
	- 5. PrefixAnnouncement encoding/decoding.

They should expose C++ API.

Internally, they can use either ndn-cpp or ndn-lite, as both are integrated in esp8266ndn.
Crypto operations may also use mbedtls of ESP32 SDK directly, which would limit these features to initially support only ESP32.

**Any specific tools or language**
- TypeScript or modern JavaScript programming for ndn-js variant.
- C++ and C programming for esp8266ndn variant.
- NFD and WiFi AP on laptop.
- Project author will loan 2x ESP32 devices.

**Expected outcomes**
- Demo NDNCERT client by requesting a certificate from a locally deployed NDNCERT CA.
- Demo certificate bundle publisher and PrefixAnnouncement encoding/decoding by packet traces.

## 4. Self-organized Network in esp8266ndn

### **[Pitch Slides]({% asset 4-esp8266ndn-junxiao.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Prefered Team Size:**
- 3

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- Many WiFi-enabled IoT devices, including the ESP8266, only support AP and STA modes, and can operate both modes simultaneously, but do not support ad hoc mode. This project explores a novel approach to organize an NDN network using only AP+STA mode.
- [esp8266ndn](https://github.com/yoursunny/esp8266ndn) is an Arduino library that enables NDN application development on ESP8266, ESP32, and nRF52 microcontrollers. Recently, @yoursunny integrated ndn-lite forwarding engine into esp8266ndn. This project will use esp8266ndn library and its ndn-lite forwarding engine.

**Briefly describe the tasks**

Organize a tree structure, rooted at a gateway that is part of the infrastructure network.
This step uses the following approach:
1. Every node operates in AP+STA mode.
2. WiFi SSID contains a number that indicates a node's distance from the gateway.
    The gateway would announce its distance to be zero.
3. Every node periodically scans nearby WiFi, and then connect to a node closer to the gateway.

Forward Interests toward the infrastructure network.
Every node is expected to know the name prefix of the wireless network, and any names not under the wireless network's prefix are considered infrastructure and forwarded up the tree via AP interface.

Forward Interests toward a wireless node.
This requires a simplified version of self-learning, where every wireless node has the same prefix length.
1. An Interest not matching any FIB entry is flooded: forward up the tree via AP interface, and multicast down the tree on STA interface.
2. Upon receiving Data from a wireless node, that node's prefix is derived from the Data name, and inserted to FIB.
3. If FIB is full, evict a random entry.
4. Keep track of the number of outstanding Interests per FIB entry, and delete a FIB entry if that count exceeds a threshold, which indicates the FIB entry could be invalid.

**Any specific tools or language**
- C++ programming for first task. C programming for second and third tasks.  NFD and WiFi AP on laptop.  Project author will loan 4x ESP8266 or ESP32 devices.

**Expected outcomes**
- Demo the system via buttons, blinking lights, or OLED displays.

## 5.  Simulating Multicast Suppression Scheme

### **[Pitch Slides]({% asset 5-multicast-ernest.pdf @path %})**

**Project Lead:**
- Ernest McCracken

**Prefered Team Size:**
- 2

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- If the algorithm is determined to be correct it can offer performance and scalability benefits to multicast situations.

**Briefly describe the tasks**
- First we will need to determine how to model multicast behavior using GameObjects.  Then we determine overall what metrics to track throughout the simulation.  Finally will be to implement the prefabs for Consumer and Producer in a manner that allows us to turn off and on the multicast suppression.

**Any specific tools or language**
- Unity3D, C#

**Expected outcomes**
- Proof showing the scheme is correct by maximizing available bandwidth while minimizing induced delay.

## 6. NDN E-MAIL

### **[Pitch Slides]({% asset 6-email-ritik.pdf @path %})**

**Project Lead:**
- Ritik Kumar, Narendra Patel

**Prefered Team Size:**
- 2

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- Stimulate the development of a centralised application, create a mailing application designed solemnly on NDN

**Briefly describe the tasks**
- Build a centralized mail server, hosted on a namespace to facilitate mail transfer on the NDN testbed.

**Any specific tools or language**
- Java, Cpp, NFD,  Postgresql, Android Studio, psync, jndn, ndn-cxx

**Expected outcomes**
- Successful mail transfer between 2 users on the same/different NDN Mail server

## 7. Service discovery for IoT devices through PSync FullSync

### **[Pitch Slides]({% asset 7-full-saurab.pdf @path %})**

**Project Lead:**
- Saurab Dulal, Ashlesh Gawande

**Prefered Team Size:**
- 2

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- Develop a PSync FullConsumer and allow IoT devices to discover services via it.

**Briefly describe the tasks**
- Finalize the design for FullConsumer and update the existing code.
- Write a simple SegmentFetcher for ESP8266.
- Port FullConsumer to ESP8266.
- Write a wrapper discovery library for PSync that allows users to publish/discover services

**Any specific tools or language**
- C++

**Expected outcomes**
- ESP8266 device can discover prefixes advertised by other nodes in sync over broadcast face.

## 8. NDN mailing List Search Tool

### **[Pitch Slides]({% asset 8-mailinglist-atif.pdf @path %})**

**Project Lead:**
- Muhammad Atif Ur Rehman

**Prefered Team Size:**
- 3

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- We aim to develop a search tool for NDN mailing lists where NDN researchers can search the question before posting it on the mailing list. For example, if someone is looking for the solution of “AdHoc faces”, then he/she may enter the key word “AdHoc faces” in the search text box, and our tool will return a list of all questions related to “AdHoc faces”, which were asked by the others before and answered by the NDN experts. It will save the time of both the person who is asking the question and the one who will answer it.

**Briefly describe the tasks**
1. NDN mailing list archives Scraper Tool: This tool will scrap all the question and answers from the NDN mailing list and store it in a database
2. Web Search Page: The search page will be the web page where NDN researchers will search the questions by entering the keywords.

**Any specific tools or language**
1. C#, Entity Framework, SQL for first task
2. HTML, CSS, JavaScript, ASP.NET MVC, Entity Framework, SQL for the second task

**Expected outcomes**
- Demo of the system by searching the NDN mailing list archive

## 9. NFD-Android Enhancements

### **[Pitch Slides]({% asset 9-android-davide.pdf @path %})**

**Project Lead:**
- Davide Pesavento

**Prefered Team Size:**
- 4

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- More and more researchers are using NDN on mobile devices; unfortunately NFD-Android is buggy and lacks several important features.

**Briefly describe the tasks**
1. Add ndnping server (#4765) and extend existing client implementation
2. Allow changing strategy choices (#3462) and content store configuration at runtime
3. Modify global NFD settings from the app: face protocols, multicast, logging, … (#2623, #2746, #4970)
4. Hub discovery improvements: Wi-Fi access point or IP gateway, DNS-SD, fix bugs, … (#3840)
5. Bug fixes and stability enhancements (#4870, #4948, …)
6. UI/UX improvements

**Any specific tools or language**
- Java or Kotlin required; prior experience in Android app development would be very useful; experience with jNDN and NFD management useful but not required.

**Expected outcomes**
- A more stable, featureful, and easier-to-use NFD app for Android, to enable the next wave of research on NDN in mobile networks.

## 10. Enhanced Testbed Monitoring and FCH Service

### **[Pitch Slides]({% asset 10-testbed-davide.pdf @path %})**

**Project Lead:**
- Davide Pesavento

**Prefered Team Size:**
- 4

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- Provide better visibility into the availability of the NDN testbed. The current status page only shows routing reachability; the redesigned page would detect data plane and prefix registration issues. Make it easier for an end host to find and connect to a working testbed router.

**Briefly describe the tasks**
1. Develop a service that periodically
	1. connects to a testbed router over UDP, TCP, and WSS,
	2. sends ndnping probes to every known destination,
	3. registers a prefix and checks its propagation by pinging from another router. Collected results should be saved into a database.
2. Develop a web application that shows the results from the database.
3. Develop an NDN-FCH compatible server that responds with routers with minimum downtime in the past T hours. This server can directly connect to the database.
4. Improve ndn-autoconfig client: try multiple routers from NDN-FCH, try the Wi-Fi access point, etc.

**Any specific tools or language**
- Python and database basics;
- C++ for the last task.

**Expected outcomes**
- Implement as much as possible of the described tasks; demonstrate the capabilities of the web app and the new NDN-FCH service.

## 11. NDN-Lite Over LoRa Network

### **[Pitch Slides]({% asset 11-lora-kent.pdf @path %})**

**Project Lead:**
- Kangheng Wu, Kent

**Prefered Team Size:**
- 3

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- More and more researchers are using NDN on IoT devices; unfortunately lacks public
information or tutorials on how to run NDN-Lite over LoRa network
- To add a LoRa adaption interface into the github project, ndn-iot-package-over-posix

**Briefly describe the tasks**
- Connect the Raspberry Pi4 device and the LoRa module with UART (Universal Asynchronous Receiver/Transmitter).
- Develop a LoRa adaption interface for NDN-Lite
- Run producer and consumer applications in Raspberry Pi4
- Improve NDN-Lite performance in the LoRa network (optional)

**Any specific tools or language**
- C language
- Project author will provide 3 RaspberryPi-4 devices and 3 LoRa modules

**Expected outcomes**
- Tutorials on how to run NDN-Lite over LoRa network
- A LoRa adaption interface for NDN-Lite

## 12. Migrate multipath forwarding strategy to latest ndnSIM and integrate ns3 TrafficControlLayer

### **[Pitch Slides]({% asset 12-ndnsim-teng.pdf @path %})**

**Project Lead:**
- Teng Liang, Klaus Schneider

**Prefered Team Size:**
- 2

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- Our proposal aims to improve ndnSIM, the simulator of NDN, by migrating multipath forwarding codebase from ndnSIM 2.1 to the latest 2.7, and integrating ns-3 TrafficControlLayer.

**Briefly describe the tasks**
1. Use ns3::TrafficControlLayer in ndn-net-device-transport module
2. Migrate Klaus code of multipath forwarding from ndnSIM 2.1 to ndnSIM 2.7
3. Integration tests with simple scenarios

**Any specific tools or language**
- C++, ndnSIM, ns-3

**Expected outcomes**
- A workable multipath forwarding strategy with an integrated traffic control layer tested in simple scenarios
