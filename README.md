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
| C-Plane | 2.7.2+ | `10b161fbb9dd81c63a29caa9d599fc50edb64e27`<br>2025.03.16 | Ubuntu<br>24.04 | 1 | 2GB | 20GB |
| UPF | 2.7.2+ | `10b161fbb9dd81c63a29caa9d599fc50edb64e27`<br>2025.03.16 | Ubuntu<br>24.04 | 1 | 1GB | 20GB |

### [free5GC](https://github.com/free5gc/free5gc)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| C-Plane | 4.0.0 | `909d7d46527c6570c153896fa58020255a0e1ca8`<br>2025.03.03<br>**(Latest nightly build on 2025.03.16)** | Ubuntu<br>24.04 | 1 | 2GB | 20GB |
| [UPF](https://github.com/free5gc/go-upf) | 1.2.6 | `07801dcf3cfd0516610aae3fa08809cfd0b2497f`<br>2025.03.03 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |
| [gtp5g](https://github.com/free5gc/gtp5g)<br>(UPF) | 0.9.12+ | `d4c2d6effe5c35bbe5bee9b7040056649aedf95a`<br>2025.03.13 | -- | -- | -- | -- |

### [UPG-VPP](https://github.com/travelping/upg-vpp)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| UPF | 1.13.0 | `dfdf64000566d35955d7c180720ff66086bd3572`<br>2024.03.25 | Ubuntu<br>22.04 | 2 | 8GB | 20GB |

### [eUPF](https://github.com/edgecomllc/eupf)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| UPF | 0.7.1+ | `8c2097ea87413f8497076a4b20f0f91d4531ac8d`<br>2025.04.16 | Ubuntu<br>24.04 | 1 | 2GB | 20GB |

### [UERANSIM](https://github.com/aligungr/UERANSIM)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 3.2.7 | `a0c3c05e81274c94b76309a7ca443dc776bd4d9b`<br>2025.02.12 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |

### [srsRAN_Project](https://github.com/srsran/srsRAN_Project)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN | 24.10+ | `2be82d8ea38e3a729850b702254952c04118cc38`<br>2025.03.14 | Ubuntu<br>24.04 | 4 | 4GB | 10GB |

### [srsRAN_4G](https://github.com/srsran/srsRAN_4G)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 23.11+ | `ec29b0c1ff79cebcbe66caa6d6b90778261c42b8`<br>2024.02.01 | Ubuntu<br>22.04 | 1 | 2GB | 10GB |

### [PacketRusher](https://github.com/HewlettPackard/PacketRusher)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 20250225+ | `2b2657337f48a2586d1a7f604ac3674085503b21`<br>2025.04.02 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |
| [gtp5g](https://github.com/free5gc/gtp5g)<br>(RAN) | 0.9.13+ | `48afb681775159e3e73ea26c736aa37bb3375157`<br>2025.04.11 | -- | -- | -- | -- |

<a id="ping_iperf3"></a>

## Ping and iPerf3

Below are the results of confirming the operation of ping and iperf3 in my environment.

<a id="5g"></a>

### For 5G

| UE | RAN | C-Plane | UPF | N3/N4/N6 | Ping | iPerf3 |
| --- | --- | --- | --- | --- | --- | --- |
| UERANSIM | UERANSIM | Open5GS | Open5GS | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[2]** | OK **[2]** |
| | | | eUPF | Separate | OK | OK |
| | | free5GC | free5GC | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[4]** | OK **[4]** |
| | | | eUPF | Separate | OK | OK |
| srsRAN_4G | srsRAN_Project | Open5GS | Open5GS | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[1][2]** | OK **[1][2]** |
| | | | eUPF | Separate | OK | OK |
| | | free5GC | free5GC | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[1][4]** | OK **[1][4]** |
| | | | eUPF | Separate | OK | OK |
| PacketRusher | PacketRusher | Open5GS | Open5GS | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[2]** | OK **[2]** |
| | | | eUPF | Separate | OK | OK **[3]** |
| | | free5GC | free5GC | Separate | OK | OK |
| | | | | Same | OK | OK |
| | | | UPG-VPP | Separate | OK **[4]** | OK **[4]** |
| | | | eUPF | Separate | OK | OK **[3]** |

<a id="4g"></a>

### For 4G

| UE | RAN | C-Plane | SGW-U | PGW-U (UPF) | S5u/Sxb/SGi | Ping | iPerf3 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| srsRAN_4G | srsRAN_4G | Open5GS | Open5GS | Open5GS | Separate | OK | OK |
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
3. When connecting PacketRusher to eUPF and using iperf3, for avoiding IP fragmentation, reduce the MTU of the N6 interface of the Data Network Gateway to 1456 bytes before the downlink packets arrive at the N6 interface of the eUPF. This 1456 bytes is 1500 bytes minus 44 bytes. The 44 bytes is the size of the headers added when eUPF encapsulates the downlink packets into GTP-U, and consists of IP Header (20 bytes), UDP Header (8 bytes) and GTP-U Header (12 bytes + 4 bytes) including one GTP-U Extension Header for QFI. See `3GPP TS 29.281 - 5 GTP-U header`. For example, if the N6 interface of the Data Network Gateway is `ens20`, set it as follows.

   ```
   # ip link set ens20 mtu 1456
   ```
4. To connect free5GC SMF to UPG-VPP, add the following parameter `nwInstFqdnEncoding: true` in `smfcfg.yaml`. See [here](https://github.com/s5uishida/enable_network_instance_encoding_free5gc_v3_3_0) for the reason.
   
   `smfcfg.yaml`
   ```
   configuration:
     nwInstFqdnEncoding: true
   ```
