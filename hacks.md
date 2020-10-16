---
layout: page
title: Hacks Proposals
---

{::options toc_levels="2,3" /}

* TOC
{:toc}

## 1. Sync Protocol Specs

### **[Pitch Slides]({% asset ndnhack10_20201013 - Proposal.pdf @path %})**

**Project Lead:**
- Junxiao Shi

<!-- Project Members: TBD -->
**Prefered Team Size:**
- 3

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- Enable interoperable implementations of these protocols.

**Briefly describe the tasks**
Write protocol specifications of three sync protocols:
- PSync FullSync
- PSync PartialSync
- syncps (Pollere Inc)

**Any specific tools or language**
- Markdown, ASCII art, Scalable Vector Graphics (SVG)

**Expected outcomes**
- Precise and unambiguous specs that match reference implementations.

## 2. RTCDataChannel Transport for Browsers

### **[Slides]({% asset ndnhack10_20201013 - Proposal.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Prefered Team Size:**
- 3

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- Better congestion control in web applications

**Briefly describe the tasks**
- RTCDataChannel transport in NDNts;
- RTCDataChannel gateway in JavaScript, Go, or C++

**Any specific tools or language**
- NDNts; wrtc, Pion, or WebRTC Native

**Expected outcomes**
- No more TCP-over-TCP in web applications

## 3. NDN Video using NDNts

### **[Pitch Slides]({% asset ndnhack10_20201013 - Proposal.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Prefered Team Size:**
- 2

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- Better video streaming application

**Briefly describe the tasks**
- Add video encoding scripts
- Embed YouTube fallback on the player page
- Explore deploying with ndn-python-repo

**Any specific tools or language**
- NDNts

**Expected outcomes**
- Better video streaming application

## 4. Passive Name Visualizer

### **[Pitch Slides]({% asset ndnhack10_20201013 - Proposal.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Prefered Team Size:**
- 3

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- Easier traffic analysis and debugging

**Briefly describe the tasks**
- Read packets from pcap.
- Parse packets.
- Visualize traffic: Traffic volume over time; Name hierarchy within selected time period.

**Any specific tools or language**
- Go language, GoPacket and NDNgo libraries; d3.js at frontend

**Expected outcomes**
- Visualization application

## 5.  NDNph – NDN-Lite Bridge

### **[Slides]({% asset ndnhack10_20201013 - Proposal.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Prefered Team Size:**
- 3

**Targeted participant**
- People new to NDN development

**How does your proposal benefit NDN?**
- Allow NDN-Lite application logic to run on platforms supported by NDNph especially, ESP32

**Briefly describe the tasks**
- Wrap NDNph as a ndn_face_intf_t on NDN-Lite side.
- Wrap NDN-Lite as a transport on NDNph side.
- Develop Mbed TLS security backend in NDN-Lite.

**Any specific tools or language**
- C and C++11; Linux; (no ESP32 necessary)

**Expected outcomes**
- Integrated library

## 6. Deploy NDNCERT v0.3 on Testbed

### **[Pitch Slides]({% asset NDNCERT_deployment_proposal.pdf @path %})**

**Project Lead:**
- Zhiyi Zhang

**Prefered Team Size:**
- 3

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- Let testbed users use new certificate management system empowered by NDNCERT v0.3

**Briefly describe the tasks**
- Work out the instructions of deploying NDNCERT on testbed, including both root CA and site CAs. 
- Exercise and improve the NDNCERT user interfaces.

**Any specific tools or language**
- C++

**Expected outcomes**
- Depoly NDNCERT at testbed

## 7. YaNFD: Yet Another NDN Forwarder

### **[Slides]({% asset YaNFD_Yet Another NDN Forwarder - Eric Newberry_proposal.pdf @path %})**

**Project Lead:**
- Eric Newberry

**Prefered Team Size:**
- 3

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- There are a number of existing forwarders for NDN. However, the most used and most generalized one of these, NFD, suffers from a number of performance and design issues. Meanwhile, other forwarders have been developed for more specific environments and scenarios, including NDN-DPDK for network backbones and ndn-lite for IoT environments. Therefore, we are in the progress of designing a new forwarder to replace NFD in general-purpose environments, such as desktops and edge servers, building upon the lessons learned while developing NFD and other forwarders.

**Briefly describe the tasks**
- Since developing a new forwarder is a massive undertaking, the goal of our hackathon project will be to sketch out a high-level design using the lessons learned from previous NDN forwarders. This will involve examining the designs and implementations of these previous forwarders and extracting principles for an improved general-purpose forwarder for NDN.

**Any specific tools or language**
- C++ (preferred), C (preferred), Go (preferred), system design, UML (preferred)

**Expected outcomes**
- We expect to develop a high-level system design for this new forwarder, including the components and the interfaces between these components. No coding should be required for this project.


## 8. Combat Fake News with screenshot verification

### **[Slides]({% asset ndn slapper_proposal.pdf @path %})**

**Project Lead:**
- Aditya Advani

**Prefered Team Size:**
- 4

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- It's about image watermarking digital published content, backporting NDN principles to today's web in a way that's instantly super useful to society.

**Briefly describe the tasks**
1. Sign published content using secure encryption method and key exchange
2. Convert the digital signature of signed content to an image watermark
3. Decrypt the watermark from a lossy image, identifying author and other relevant publication details

**Any specific tools or language**
- Anything contemporary or dynamic is fine. Python or JavaScript ideal. 

**Expected outcomes**
- Basically I would like to create a simple way to image watermark mixed images and text content like tweets so that I can make a PoC showing how all social media and all apps including most websites should incorporate this technology immediately. Backporting NDN principles to today's web.

I came up with the idea on Aaron Swartz Day in 2018 while watching Chelsea Manning speak in person. Only discovered NDN last night so very excited at the prospect of having real CS grad students help me! Been searching for this kind of support for a year now, see:
https://medium.com/@aditya_advani/how-to-defeat-fake-news-with-a-screenshot-verification-service-svs-e80867dfbc58

## 9. NFD Strategy Plugin System

### **[Slides]({% asset NFD_strategy_Plugin_proposal.pdf @path %})**

**Project Lead:**
- Ashlesh Gawande, Saurab Dulal

**Prefered Team Size:**
- 2

**Targeted participant**
- People with NDN code development experience

**How does your proposal benefit NDN?**
- Creating a strategy plugin system (like Linux Kernel Modules or Video Game Mods), would let NFD load a strategy at run time from a shared object le.
- Running experiments on testbed with new strategies will be easier and bug x deployment will be faster."

**Briefly describe the tasks**
- Compile NFD (or strategies?) as a library
- Modify NFD to look for shared objects and load/unload the strategy
from them
- Add or modify NFD tools as required to load/unload strategies

**Any specific tools or language**
- C, C++14, NFD

**Expected outcomes**
- C, C++14, NFD, waf build system
