# Simple Confirmed Information for Mobile Network

This is a memo of environment information when briefly confirming the operation of some functions of each open source. Please note that it may not work depending on the environment.
Also, please note that there may be cases where I have not been able to confirm operation due to my settings being incorrect.

---

### [Sample Configurations and Miscellaneous for Mobile Network](https://github.com/s5uishida/sample_config_misc_for_mobile_network)

---

<a id="toc"></a>

## Table of Contents

- [Version and Resource requirements](#version_resource)
- [Ping and iPerf3](#ping_iperf3)
  - [For 5G](#5g)
  - [For 4G](#4g)

---
<a id="version_resource"></a>

## Version and Resource requirements

### [Open5GS](https://github.com/open5gs/open5gs)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| C-Plane | 2.7.6+ | `d7875898895f17c386f2057e4a201411098a398b`<br>2025.08.03 | Ubuntu<br>24.04 | 1 | 2GB | 20GB |
| UPF | 2.7.6+ | `d7875898895f17c386f2057e4a201411098a398b`<br>2025.08.03 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |

**Note. In [the next commit version](https://github.com/open5gs/open5gs/commit/417f6e0e56cf928b503c26421522a81321307e99) above, PFCP communication with eUPF did not work properly.**

### [free5GC](https://github.com/free5gc/free5gc)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| C-Plane | 4.2.0+ | `8458edbcacd083d5d4777d197aa9c125e122cd40`<br>2026.01.14<br>**(Latest nightly build on 2026.01.17)** | Ubuntu<br>24.04 | 1 | 2GB | 20GB |
| [UPF](https://github.com/free5gc/go-upf) | 1.2.8 | `b798fe5ee6a984be492fa53958dd5f1305469f85`<br>2026.01.05 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |
| [gtp5g](https://github.com/free5gc/gtp5g)<br>(UPF) | 0.9.16 | `8d723c29fc0de3eeeff3e9a91132838579e8ee1b`<br>2025.12.02 | -- | -- | -- | -- |

**Note. Built free5GC with Go 1.24.12.**

### [UPG-VPP](https://github.com/travelping/upg-vpp)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| UPF | 1.13.0<br>(+[patch](https://github.com/s5uishida/install_vpp_upf_dpdk#pdu_session_container_qfi)) | `dfdf64000566d35955d7c180720ff66086bd3572`<br>2024.03.25 | Ubuntu<br>22.04 | 2 | 8GB | 20GB |

### [eUPF](https://github.com/edgecomllc/eupf)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| UPF | 0.7.1+ | `a8d774a0533ad71ddd59899be26f4aee8a31b5d2`<br>2025.06.16 | Ubuntu<br>24.04 | 1 | 2GB | 10GB |

### [OAI-CN5G-UPF](https://gitlab.eurecom.fr/oai/cn5g/oai-cn5g-upf)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| UPF | 2.2.0<br>(+[patch](https://github.com/s5uishida/install_oai_upf/tree/main#get_patch)) | `e025cdfb3a9c18a228f2efe36bd06b9de998554c`<br>2025.12.13 | Ubuntu<br>24.04 | 1 | 6GB | 20GB |

### [UERANSIM](https://github.com/aligungr/UERANSIM)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 3.2.7+ | `b4157fa9413a083a3b996c694067a011751fae82`<br>2025.10.25 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |

### [srsRAN_Project](https://github.com/srsran/srsRAN_Project)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN | 25.10 | `d2f4b70dda8e2c557d5b05a0ac5f92dbddda19bc`<br>2025.11.11 | Ubuntu<br>24.04 | 5 | 4GB | 10GB |

### [srsRAN_4G](https://github.com/srsran/srsRAN_4G)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 23.11+ | `1fab3df863f66fdb6c3b34f1b39e745dbcb12d5e`<br>2025.10.22 | Ubuntu<br>24.04 | 1 | 2GB | 10GB |

### [PacketRusher](https://github.com/HewlettPackard/PacketRusher)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 20250225+ | `2f625c61b7109a3786dc86881f8c284f724469ba`<br>2025.12.09 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |
| [gtp5g](https://github.com/free5gc/gtp5g)<br>(RAN) | 0.9.16 | `8d723c29fc0de3eeeff3e9a91132838579e8ee1b`<br>2025.12.02 | -- | -- | -- | -- |

<a id="ping_iperf3"></a>

## Ping and iPerf3

Below are the results of confirming the operation of ping and iperf3 in my environment.

<a id="5g"></a>

### For 5G

| UE | RAN | C-Plane | UPF | N3/N4/N6 | Ping | iPerf3 |
| --- | --- | --- | --- | --- | --- | --- |
| UERANSIM **[4]** | UERANSIM | Open5GS | Open5GS | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[2]** | OK **[2]** |
| | | | eUPF | Separate | OK | OK |
| | | | OAI-CN5G-UPF | Separate | OK **[2]** | OK **[2]** |
| | | free5GC | free5GC | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[3]** | OK **[3]** |
| | | | eUPF | Separate | OK | OK |
| | | | OAI-CN5G-UPF | Separate | OK | OK |
| srsRAN_4G **[5]** | srsRAN_Project | Open5GS | Open5GS | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[1][2]** | OK **[1][2]** |
| | | | eUPF | Separate | OK | OK |
| | | | OAI-CN5G-UPF | Separate | -- | -- |
| | | free5GC | free5GC | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[1][3]** | OK **[1][3]** |
| | | | eUPF | Separate | OK | OK |
| | | | OAI-CN5G-UPF | Separate | -- | -- |
| PacketRusher **[6]** | PacketRusher | Open5GS | Open5GS | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[2]** | OK **[2]** |
| | | | eUPF | Separate | OK | OK |
| | | | OAI-CN5G-UPF | Separate | OK **[2]** | OK **[2]** |
| | | free5GC | free5GC | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[3]** | OK **[3]** |
| | | | eUPF | Separate | OK | OK |
| | | | OAI-CN5G-UPF | Separate | OK | OK |

<a id="4g"></a>

### For 4G

| UE | RAN | C-Plane | SGW-U | PGW-U (UPF) | S5u/Sxb/SGi | Ping | iPerf3 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| srsRAN_4G **[7]** | srsRAN_4G | Open5GS | Open5GS | Open5GS | Separate | OK | OK |
| | | | | | Same | OK | OK |
| | | | | UPG-VPP | Separate | OK **[2]** | OK **[2]** |
| | | | | eUPF | Separate | OK | OK |

<a id="footnotes"></a>

1. UPG-VPP v1.13.0 does not support `PDU Session container`. Therefore, some gNodeBs such as srsRAN_Project, may not accept GTP traffic from UPG-VPP. In that case, please refer to [this](https://github.com/s5uishida/install_vpp_upf_dpdk/tree/main#build-upg-vpp-v1130) note. In these results, I applied this temporary patch and confirmed that it worked with the gNodeB of srsRAN_Project.
2. To connect Open5GS SMF to UPG-VPP, add the following parameter `use_upg_vpp: true` in `smf.yaml`. See [here](https://github.com/open5gs/open5gs/discussions/3591#discussioncomment-11369302) for the reason.
   
   `smf.yaml`
   ```
   global:
     parameter:
       use_upg_vpp: true
   ```
3. To connect free5GC SMF to UPG-VPP, add the following parameter `nwInstFqdnEncoding: true` in `smfcfg.yaml`. See [here](https://github.com/s5uishida/enable_network_instance_encoding_free5gc_v3_3_0) for the reason.
   
   `smfcfg.yaml`
   ```
   configuration:
     nwInstFqdnEncoding: true
   ```
4. The MTU of the tunnel interface of UERANSIM is fixed at 1400 bytes.
5. The MTU of the tunnel interface of srsRAN_4G NR-UE is 1500 bytes by default. With this value, uplink packets are fragmented at srsRAN_Project gNodeB. So for avoiding IP fragmentation, reduce the MTU of the tunnel interface of srsRAN_4G NR-UE to 1456 bytes. This 1456 bytes is 1500 bytes minus 44 bytes. The 44 bytes is the size of the headers added when srsRAN_Project gNodeB encapsulates the uplink packets into GTP-U, and consists of IP Header (20 bytes), UDP Header (8 bytes) and GTP-U Header (12 bytes + 4 bytes) including one GTP-U Extension Header for QFI. See `3GPP TS 29.281 - 5 GTP-U header`. For example, if the tunnel interface of srsRAN_4G NR-UE is `tun_srsue`, set it as follows.

   ```
   # ip link set tun_srsue mtu 1456
   ```
6. The MTU of the tunnel interface of PacketRusher NR-UE is 1464 bytes by default. With this value, uplink packets are fragmented at the gNodeB equivalent function in PacketRusher. So for avoiding IP fragmentation, reduce the MTU of the tunnel interface of PacketRusher NR-UE to 1456 bytes. This 1456 bytes is the same meaning as the value explained in **[5]**. For example, if the interface assigned to VRF of PacketRusher is `val0000001000`, set it as follows.

   ```
   # ip link set val0000001000 mtu 1456
   ```
7. The MTU of the tunnel interface of srsRAN_4G UE is 1500 bytes by default. With this value, uplink packets are fragmented at srsRAN_4G eNodeB. So for avoiding IP fragmentation, reduce the MTU of the tunnel interface of srsRAN_4G UE to 1464 bytes. This 1464 bytes is 1500 bytes minus 36 bytes. The 36 bytes is the size of the headers added when srsRAN_4G eNodeB encapsulates the uplink packets into GTP-U, and consists of IP Header (20 bytes), UDP Header (8 bytes) and GTP-U Header (8 bytes, No Sequence Number and No GTP-U Extension Header). See `3GPP TS 29.281 - 5 GTP-U header`. For example, if the tunnel interface of srsRAN_4G UE is `tun_srsue`, set it as follows.

   ```
   # ip link set tun_srsue mtu 1464
   ```
