# CSC458 – Programming Assignment 1: Network Interface

Individual assignment for University of Toronto's CSC458 (Computer Networks), implementing the network interface that translates between IP datagrams and Ethernet frames, including ARP resolution. Built on the Stanford CS144 ("Sponge") TCP/IP stack framework. This module is later reused unchanged as part of the router in [PA2](https://github.com/Baaadmtfka/CSC458_Computer_Networks-A2).

## What's in this repo

Only the module written for this assignment is included here — the course-provided framework (headers like `address.hh`, `arp_message.hh`, `ethernet_frame.hh`, `ipv4_datagram.hh`, the CMake build, and the test suite) is not part of this repo, since it isn't student-authored. As a result this code **isn't buildable standalone**.

### `network_interface.cc` / `.hh`

- `send_datagram`: looks up the next hop's MAC address in the ARP cache. If unknown, queues the datagram and broadcasts an ARP request (cached IP→MAC mappings expire after 30s; a pending ARP request is not re-sent for 5s).
- `recv_frame`: for IPv4 frames addressed to this interface, returns the parsed datagram up the stack. For ARP requests/replies, learns the sender's IP→MAC mapping, answers requests targeted at this interface, and flushes any datagrams that were queued waiting on that resolution. Uses a helper, `arp_msg_handler`, to keep this logic separated from frame validation.
- `tick`: ages out expired ARP cache entries and pending ARP requests.

Two supporting structs track state: `ARPCacheEntry` (learned IP→MAC mappings with a TTL) and `ARPRequestEntry` (a TTL plus the queue of datagrams waiting on a pending ARP resolution).

## Design notes

See [pa1.md](pa1.md) for the original assignment writeup (design rationale, time spent, and known issues).

## Author

Zixuan Zeng
