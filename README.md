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
| C-Plane | 2.7.2+ | `606788361cb2255961f856de17d71c6b2fc86847`<br>2024.10.11 | Ubuntu<br>24.04 | 1 | 2GB | 20GB |
| UPF | 2.7.2+ | `606788361cb2255961f856de17d71c6b2fc86847`<br>2024.10.11 | Ubuntu<br>24.04 | 1 | 1GB | 20GB |

### [free5GC](https://github.com/free5gc/free5gc)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| C-Plane | 3.4.3+ | `9675d563ac90ec2193ccbbdd700b0fb534a4165b`<br>2024.10.11<br>**(Latest nightly build on 2024.10.14)** | Ubuntu<br>24.04 | 1 | 2GB | 20GB |
| [UPF](https://github.com/free5gc/go-upf) | 1.2.3 | `6b73d126b8b29b4d17ff744c31ef50634ee64164`<br>2024.10.11 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |
| [gtp5g](https://github.com/free5gc/gtp5g)<br>(UPF) | 0.8.10 | `3ee1a5262c5b4dc2ba118b7cb1ed0ba842d3b07b`<br>2024.06.03 | -- | -- | -- | -- |

### [UPG-VPP](https://github.com/travelping/upg-vpp)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| UPF | 1.13.0 | `dfdf64000566d35955d7c180720ff66086bd3572`<br>2024.03.25 | Ubuntu<br>22.04 | 2 | 8GB | 20GB |

### [eUPF](https://github.com/edgecomllc/eupf)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| UPF | 0.6.4 | `55ce219c09776470f9a8f66bea020466a61e4e87`<br>2024.09.22 | Ubuntu<br>24.04 | 1 | 2GB | 20GB |

### [OsmoUPF](https://gitea.osmocom.org/cellular-infrastructure/osmo-upf)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| UPF | 0.1.1.109 | `6859de09d2ae0e363070e152489d9f8579085aa8`<br>2024.08.16 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |

### [UERANSIM](https://github.com/aligungr/UERANSIM)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 3.2.6+ | `528061fe10389876da58d3bd15e8cba6d7c152a9`<br>2024.08.27 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |

### [srsRAN_Project](https://github.com/srsran/srsRAN_Project)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN | 24.04+ | `4ac5300d4927b5199af69e6bc2e55d061fc33652`<br>2024.07.31 | Ubuntu<br>24.04 | 2 | 4GB | 10GB |

### [srsRAN_4G](https://github.com/srsran/srsRAN_4G)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 23.11+ | `ec29b0c1ff79cebcbe66caa6d6b90778261c42b8`<br>2024.02.01 | Ubuntu<br>22.04 | 1 | 2GB | 10GB |

### [PacketRusher](https://github.com/HewlettPackard/PacketRusher)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 20240521+ | `32a08fa9fb2d83b654628b5187a0244a66b737b2`<br>2024.06.24 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |
| [gtp5g](https://github.com/free5gc/gtp5g)<br>(RAN) | 0.8.6 | `d8818ee80a9a004ea0fac3715415395810666921`<br>2024.02.18 | -- | -- | -- | -- |
|| 0.9.2 **[1]** | `0ec00843e79ff4660a43fbeddf2ae730414dee5c`<br>2024.10.11 | -- | -- | -- | -- |

1. In gtp5g v0.8.7 and later, GTP-U Sequence Number is enabled by default. In this case, eUPF will probably not be able to process GTP-U packets correctly. Therefore, if connecting to eUPF, please disable GTP-U Sequence Number of gtp5g used by PacketRusher as follows.
   
   ```
   # echo 0 > /proc/gtp5g/seq
   ```
   Also, UPF performance measurements using iperf3 tended to be better when GTP-U Sequence Number was disabled. (e.g. UPG-VPP)

<a id="ping_iperf3"></a>

## Ping and iPerf3

Below are the results of confirming the operation of ping and iperf3 in my environment.

<a id="5g"></a>

### For 5G

| UE | RAN | C-Plane | UPF | N3/N4/N6 | Ping | iPerf3 |
| --- | --- | --- | --- | --- | --- | --- |
| UERANSIM | UERANSIM | Open5GS | Open5GS | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK | OK |
| | | | eUPF | Separate | OK | OK |
| | | | OsmoUPF | Separate | NG | NG |
| | | free5GC | free5GC | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK | OK |
| | | | eUPF | Separate | OK | OK |
| | | | OsmoUPF | Separate | NG | NG |
| srsRAN_4G | srsRAN_Project | Open5GS | Open5GS | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[2]** | OK **[2]** |
| | | | eUPF | Separate | OK | OK **[3]** |
| | | | OsmoUPF | Separate | NG | NG |
| | | free5GC | free5GC | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[2]** | OK **[2]** |
| | | | eUPF | Separate | OK | OK **[3]** |
| | | | OsmoUPF | Separate | NG | NG |
| PacketRusher | PacketRusher | Open5GS | Open5GS | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK | OK |
| | | | eUPF | Separate | OK **[1]** | OK **[1]** |
| | | | OsmoUPF | Separate | OK | OK |
| | | free5GC | free5GC | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK | OK |
| | | | eUPF | Separate | OK **[1]** | OK **[1]** |
| | | | OsmoUPF | Separate | OK | OK |

<a id="4g"></a>

### For 4G

| UE | RAN | C-Plane | SGW-U | PGW-U (UPF) | S5u/Sxb/SGi | Ping | iPerf3 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| srsRAN_4G | srsRAN_4G | Open5GS | Open5GS | Open5GS | Separate | OK | OK |
| | | | | | Same | OK | OK |
| | | | | UPG-VPP | Separate | OK | OK |
| | | | | eUPF | Separate | OK | OK **[3]** |
| | | | | OsmoUPF | Separate | OK | OK |

2. UPG-VPP v1.13.0 does not support `PDU Session container`. Therefore, some gNodeBs such as srsRAN_Project, may not accept GTP traffic from UPG-VPP. In that case, please refer to [this](https://github.com/s5uishida/install_vpp_upf_dpdk/tree/main#build-upg-vpp-v1130) note. In these results, I applied this temporary patch and confirmed that it worked with the gNodeB of srsRAN_Project.
3. To avoid IP fragmentation, change the MTU of `tun_srsue` interface of srsRAN_4G UE as follows.
   
   ```
   # ip link set tun_srsue mtu 1450
   ```
