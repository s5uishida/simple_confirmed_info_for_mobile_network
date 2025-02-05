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
| C-Plane | 2.7.2+ | `13585a34e3d5505dd86d2cdf78c91829f3936851`<br>2025.01.12 | Ubuntu<br>24.04 | 1 | 2GB | 20GB |
| UPF | 2.7.2+ | `13585a34e3d5505dd86d2cdf78c91829f3936851`<br>2025.01.12 | Ubuntu<br>24.04 | 1 | 1GB | 20GB |

### [free5GC](https://github.com/free5gc/free5gc)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| C-Plane | 3.4.4+ | `f9ebb11738a6efa0f6885299be0cc46aeeadecfd`<br>2025.01.03<br>**(Latest nightly build on 2025.02.05)** | Ubuntu<br>24.04 | 1 | 2GB | 20GB |
| [SMF](https://github.com/free5gc/smf)<br>(ULCL) | 1.2.6+ | `d049a7aa51db56cb2fad33713e422deac77ee2eb`<br>2025.01.23<br>**+https://github.com/free5gc/smf/pull/147** | -- | -- | -- | -- |
| [UPF](https://github.com/free5gc/go-upf) | 1.2.4+ | `88fbd8bb7b86761cbbcf1367acf2df7d81392ce3`<br>2025.01.02 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |
| [gtp5g](https://github.com/free5gc/gtp5g)<br>(UPF) | 0.9.11 | `4993e7c5e69e062b1e9bc60e5df3ed243aa5f6d1`<br>2025.01.24 | -- | -- | -- | -- |

### [UPG-VPP](https://github.com/travelping/upg-vpp)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| UPF | 1.13.0 | `dfdf64000566d35955d7c180720ff66086bd3572`<br>2024.03.25 | Ubuntu<br>22.04 | 2 | 8GB | 20GB |

### [eUPF](https://github.com/edgecomllc/eupf)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| UPF | 0.6.4+ | `307b80aec8c7bc8fa376e03927c2f5c55a1fd687`<br>2024.12.23 | Ubuntu<br>24.04 | 1 | 2GB | 20GB |

### [UERANSIM](https://github.com/aligungr/UERANSIM)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 3.2.6+ | `01e3785420ff7db34fa8723ff34189b8372cf02e`<br>2024.12.10 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |

### [srsRAN_Project](https://github.com/srsran/srsRAN_Project)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN | 24.10+ | `e5d5b44b92cf18d1bd1736da0148e5f9cce3721d`<br>2024.12.03 | Ubuntu<br>24.04 | 4 | 4GB | 10GB |

### [srsRAN_4G](https://github.com/srsran/srsRAN_4G)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 23.11+ | `ec29b0c1ff79cebcbe66caa6d6b90778261c42b8`<br>2024.02.01 | Ubuntu<br>22.04 | 1 | 2GB | 10GB |

### [PacketRusher](https://github.com/HewlettPackard/PacketRusher)

| Role | Version | Commit & Date | OS | CPU<br>(Min) | Mem<br>(Min) | HDD<br>(Min) |
| --- | --- | --- | --- | --- | --- | --- |
| RAN & UE | 20240521+ | `fd83fec05d964cab7a16fe0d55ff230dd6d9a77a`<br>2024.11.27 | Ubuntu<br>24.04 | 1 | 1GB | 10GB |
| [gtp5g](https://github.com/free5gc/gtp5g)<br>(RAN) | 0.9.11 | `4993e7c5e69e062b1e9bc60e5df3ed243aa5f6d1`<br>2025.01.24 | -- | -- | -- | -- |

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
3. When connecting PacketRusher to eUPF and using iperf3, for avoiding IP fragmentation, reduce the MTU of the N6 interface of the Data Network Gateway to 1450 bytes before the downlink packet reaches the N6 interface of the eUPF. For example, if the N6 interface of the Data Network Gateway is `ens20`, set it as follows.

   ```
   # ip link set ens20 mtu 1450
   ```
4. To connect free5GC SMF to UPG-VPP, add the following parameter `nwInstFqdnEncoding: true` in `smfcfg.yaml`. See [here](https://github.com/s5uishida/enable_network_instance_encoding_free5gc_v3_3_0) for the reason.
   
   `smfcfg.yaml`
   ```
   configuration:
     nwInstFqdnEncoding: true
   ```
