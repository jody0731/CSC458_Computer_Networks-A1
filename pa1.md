Programming Assignment 1 Writeup
====================

My name: ZIXUAN ZENG

My UTORID: 1008533419

My email address: zixuan.zeng@mail.utoronto.ca


I collaborated with: [No one.] 
// List everybody who you discussed the assignment with here. Please remember the academic integrity policies discussed in Handout #1. 

I used the following tools: [ChatGPT o3-mini] 
for C++ naming conventions, pointer usages, variable initializations.
// List any AI and code generation tools you may have used here.

I would like to credit/thank these classmates for their help: [No one.]

This programming assignment took me about [8] hours to complete.

Program Structure and Design of the NetworkInterface:
The program structure followed the basic program outline instructions. 
Comments within code are detailed.
To maintain a clean Coding Style, a helper function (arp_msg_handler) is used for (recv_frame).
Two new structs: (ARPCacheEntry) for ARP cache table, and (ARPRequestEntry) for storing datagrams for ARP requests.
Three new variables within the NetworkInterface class: (_arp_table) for mapping IP address to ARPCacheEntry, (_arp_request_table) for mapping IP address to ARPRequestEntry, (_frames_ready) for ready-to-send queue.
// Describe the structure of your code and any design decisions you made that you think the graders need to be aware of.

Implementation Challenges:
// Describe any issues you encountered that might have had an impact on the performance of your solution, but you managed to address. 
The handout was somewhat unclear on what message needs to be sent in recv_frame when receiving an ARP message.

Remaining Bugs:
// Describe any remaining bugs/issues that still remain in your code.
All public tests passed, with Total Test time (real) = 2.05 sec.