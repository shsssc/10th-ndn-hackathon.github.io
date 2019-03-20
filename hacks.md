---
layout: page
title: Hacks Proposals
---

{::options toc_levels="2,3" /}

* TOC
{:toc}


## <del>1. ESP32 Video Doorbell</del>>

### **[Pitch Slides](https://drive.google.com/file/d/1B-0FBrOfQBRtXzIqesaLxJL4RIm_hf57/view)**

Project Lead: Junxiao Shi

<!-- Project Members: TBD -->
Prefered Team Size: 2

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

3. NDN library: https://github.com/yoursunny/esp8266ndn 
Camera library: https://github.com/yoursunny/ESP32-CAM-OV2640

**Any specific tools or language**
- Project author will loan 1x ODROID-GO, 1x ESP32-CAM, 1x USB-UART, 1x button. Each task needs 1 participant who can write C++.

**Expected outcomes**
- Finish all tasks.


## 2. Enhance Testbed Status Page and NDN-FCH Service

### **[Slides]({% asset 2-NDN-Testbed-Monitoring-tool.pdf @path %})**

Project Lead: Junxiao Shi, Davide Pesavento

<!-- Project Members: TBD -->
Prefered Team Size: 3

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- Provide better visibility into the availability of the global NDN testbed. Current status page http://ndndemo.arl.wustl.edu only shows node availability and routing reachability. Redesigned status page would detect data plane and prefix registration problems.  Make it easier for an end host to find an operational testbed router. ndn-autoconfig and NDN-JS should try multiple routers learned from NDN-FCH.

**Briefly describe the tasks**
1. Develop a backend service to (1) connect to a testbed router over UDP, TCP, and TLS-WebSocket, (2) send ndnping probes to every known destination, (3) register a prefix and check its propagation by sending ndnping probes from another router.
The results should be saved into a PostgreSQL database for accountability and analysis.

2. Develop a web application that shows the results from the database.

3. Develop an NDN-FCH compatible server that responds with routers with minimum downtime in the past 3 hours.
This server can directly connect to the database.

4. Modify ndn-autoconfig program to retrieve multiple routers from an NDN-FCH service, and try each only until establishing data plane reachability.
Also, ndn-autoconfig should try the WiFi access point as a potential NDN router, before executing NDN-FCH stage.

5. Modify NDN-JS Face class to use NDN-FCH service instead of trying to connect to *.ws.ndn.ucla.edu hostnames.

**Any specific tools or language**
- Backend, webapp, NDN-FCH tasks need 2 participants who can write Python. ndn-autoconfig task needs 0.5 participant who can write C++. NDN-JS task needs 0.5 participant who can write JavaScript.

**Expected outcomes**
- Finish all tasks.

## 3. Four-Layer Improvement of esp8266ndn

### **[Slides](https://github.com/8th-ndn-hackathon/esp8266ndn-nrf52/blob/master/README.md)**

Project Lead: Junxiao Shi

<!-- Project Members: TBD -->
Prefered Team Size: 5

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- esp8266ndn is an Arduino library that enables NDN application development on ESP8266 and ESP32 microcontrollers. https://github.com/yoursunny/esp8266ndn  This project improves esp8266ndn in four layers. L5: add PSync PartialSync consumer. L3: experiment with Bloom Filter based Forwarder that performs NDN forwarding in fixed amount of memory. L2: Python proxy program to bring BLE to NFD. L1: tune LoRa parameters. Multi-Layer: port the library to nRF52 boards.

**Briefly describe the tasks**
1. ML
Make the library compile with Arduino core for Adafruit Bluefruit nRF52 boards, without breaking existing ESP8266 and ESP32 support.
Send and receive packets over Bluetooth Low Energy as GATT attributes, using same protocol as the existing ESP32 implementation.
Crypto is excluded in this project.

2. L5
Implement a PSync PartialSync consumer.

3. L3
Explore a Bloom Filter based NDN forwarder design that performs NDN forwarding using a fixed amount of memory.
The design will be provided in a separate document.
Bloom Filter library: https://github.com/yoursunny/hsip-bf

4. L2
Develop a Python proxy program with PyNDN2 and bluepy libraries to bridge between NFD's Unix socket face and a BLE connection to ESP32 or nRF52.
Reference: BlePingClient.py in esp8266ndn repository.

5. L1
Study how different LoRa parameters affect signal range and packet loss rate.
Tune the existing LoRa transport to make it work better in indoor and outdoor environment.

**Any specific tools or language**
- Project author will loan 2x nRF52832, 3x ESP32 WiFi+BLE+LoRa, 3x ESP32 WiFi+BLE, and 1x BLE-capable NDN router. ML task needs 1.5 participant who can write C++. L5 task needs 1 participant who can write C++. L3 task needs 1.5 participant who understands algorithms and can write C++. L2 task needs 0.5 participant who can write simple Python. L1 task needs 0.5 participant who can walk 1 kilometer and back several times.

**Expected outcomes**
- Finish half of the tasks.

## 4. Implementing the new Signed Interest in ndn-lite

### **[Slides]({% asset 4-A-half-done-Sigcomm-Tutorial-App.pdf @path %})**

Project Lead: Zhiyi Zhang

<!-- Project Members: TBD -->
Prefered Team Size: 2

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- New Feature

**Briefly describe the tasks**
1. Implement the signed Interest according to the new signed Interest format

**Any specific tools or language**
- C

**Expected outcomes**
- Implemented and Tested

## 5. NDN-Lite: Integrate Service Discovery and Access Control and Schematized Trust

### **[Slides]({% asset 4-A-half-done-Sigcomm-Tutorial-App.pdf @path %})**

Project Lead: Zhiyi Zhang

<!-- Project Members: TBD -->
Prefered Team Size: 4

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- Make NDN-Lite available to Raspberry Pi owners and MacOS users. 

- Prepare for the sigcomm tutorial

**Briefly describe the tasks**
1. Make NDN-Lite available to Raspberry Pi  

2. Coding

**Any specific tools or language**
- C

**Expected outcomes**
- Cool Demo of these three functions provided by ndn-lite

## 6. NFD-Android Enhancements

### **[Slides]({% asset 6-NFD-Android-Enhancements.pdf @path %})**

Project Lead: Davide Pesavento

<!-- Project Members: TBD -->
Prefered Team Size: 4

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- More and more researchers are using NDN on mobile devices; unfortunately NFD-Android is buggy and lacks several important features

**Briefly describe the tasks**
1. Add ndnping server (#4765) and extend existing client implementation

2. Allow changing strategy choices (#3462) and content store configuration at runtime

3. Modify global NFD settings from the app: face protocols, multicast, logging, … (#2623, #2746)

4. Hub discovery improvements: Wi-Fi access point or IP gateway, DNS-SD, fix bugs, … (#3840, #4028)

5. Bug fixes and stability enhancements (#4688, #4628, #3409, …)

6. UI/UX improvements

**Any specific tools or language**
- Java/Kotlin, Android, jNDN, NFD management

**Expected outcomes**
- Java/Kotlin, Android, jNDN, NFD management

## 7. Self-Learning for Ad Hoc Wireless Networks

### **[Slides]({% asset 7-Self-Learning-for-Ad-Hoc-Wireless-Networks.pdf @path %})**

Project Lead: Davide Pesavento, Md Ashiqur Rahman

<!-- Project Members: TBD -->
Prefered Team Size: 3

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- There is a strong desire from multiple research groups to use self-learning in ad hoc wireless networks, or more generally on broadcast links. However, the initial version of self-learning released with NFD 0.6.5 supports only point-to-point links (e.g., unicast Ethernet in wired networks).

**Briefly describe the tasks**
1. Ethernet multicast face refactoring (#4283)

2. Finish adding EndpointId to the relevant APIs (#4843, #4849)

3. Implement self-learning strategy version 2 (#4281)

**Any specific tools or language**
- C++, NFD internals (faces, forwarding, strategy API)

**Expected outcomes**
- Self-learning can be used in ad hoc wireless networks, including automatic switching from multicast to unicast. If feasible, give a basic demonstration of the new forwarding strategy.

## <del>8. Attribute Based Signature Scheme for NDN</del>

### **[Pitch Slides](https://drive.google.com/file/d/1H8awzvgfIn_FBpnpmaLm_JCb-r53G_Rw/view)**

Project Lead: Sanjeev Kaushik Ramani

<!-- Project Members: TBD -->
Prefered Team Size: 3

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- New signature scheme that can be used in the ICE-AR project

**Briefly describe the tasks**
- Implement Attribute Based Signature Scheme in NDN

**Any specific tools or language**
- C++

**Expected outcomes**
- Be able to sign packets using attributes and predicates.

## 9. PSync for Repos

### **[Slides]({% asset 9-PSync-Hackathon-2019.pdf @path %})**

Project Lead: Jeff Thompson

<!-- Project Members: TBD -->
Prefered Team Size: 3

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- Robust synchronization of names enabling repo storage and multiuser discovery of content.

**Briefly describe the tasks**
1. Make a version of the PSync FullProducer class which allows arbitrary names w/o sequence numbers.

2. Test robustness under a set of many names. Compare performance with names with sequence numbers.

**Any specific tools or language**
- ndn-cxx, basic NDN interest/data exchange, sync protocols.

**Expected outcomes**
- An updated PSync library with Full PSync of arbitrary names, at https://github.com/named-data/PSync 

- Demo app showing repo fetching of data for new names announced by a producer.

## <del>10. Enhancements for npChat Android application</del>

### **[Pitch Slides](https://drive.google.com/file/d/1trb9waSkIvfu3iwtF1iYAJ2vi0yebRko/view)**

Project Lead: Ashlesh Gawande

<!-- Project Members: TBD -->
Prefered Team Size: 3

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- Add pipelining to jNDN similar to ndn-cxx SegmentFetcher. Make more use of jNDN functionalities.

**Briefly describe the tasks**
1. Add fixed and aimd pipelining to jNDN SegmentFetcher along with unit tests. 

2. Replace npChat’s FaceProxy class with MemoryContentCache or InMemoryStorageRetaining to serve data.

3. Modify npChat to collect timing information.

**Any specific tools or language**
- Java, jNDN, NFD-android, Android app development

**Expected outcomes**
- Demonstrate better performance of npChat app while fetching media.

## 11. Fix Ndncatchunks Performance Issues

### **[Slides]({% asset 11-catchunks_perf.pdf @path %})**

Project Lead: Klaus Schneider

<!-- Project Members: TBD -->
Prefered Team Size: 4

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- Improve performance of NDN applications

**Briefly describe the tasks**
- Evaluate ndncatchunks to see what causes the performance issues, and then implement and test the solution.

**Any specific tools or language**
- C++, NFD, tc netem.

**Expected outcomes**
- Evaluate ndncatchunks to see what causes the performance issues, and then implement and test the solution.

## 12. Improve the Wireshark dissector for NDN

### **[Slides]({% asset 12-Wireshark-Dissector.pdf @path %})**

Project Lead: Davide Pesavento

<!-- Project Members: TBD -->
Prefered Team Size: 2

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- The Wireshark dissector is a fundamental tool for NDN developers, operators, and experimenters, yet it is still incomplete and unusable in several common cases

**Briefly describe the tasks**
1. Make TLV-TYPE decoding context-aware

2. Reassemble NDNLP-fragmented packets

3. Decode NDN packets spanning multiple TCP segments

4. Improve info displayed on unrecognized and out-of-order TLV elements

5. Produce sample pcap traces for all the above cases (for testing)

**Any specific tools or language**
- No

**Expected outcomes**
- Show screenshots (or live demo) comparing the information displayed by Wireshark on a variety of packet traces before and after the improvements

## 13. Vector Sync for MANET

### **[Slides]({% asset 13-Sync-in-MANET-Library+Demo.pdf @path %})**

Project Lead: Tianxiang Li

<!-- Project Members: TBD -->
Prefered Team Size: 3

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- For testing Sync Protocol performance in MANET scenarios using Raspberry Pis. This project is aimed to be incorporated with data centric MAC(VMAC) for neighbor discovery and layer 2 name based filtering. 

**Briefly describe the tasks**
1. Implement a basic version of Vector Sync for MANET.

2. Have a working version of Vector Sync on Raspberry Pis for testing in MANET scenario.

**Any specific tools or language**
- c++

**Expected outcomes**
- Vector Sync Library with basic functions.

- Import library to Raspberry Pis for testing.
