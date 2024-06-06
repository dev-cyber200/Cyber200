+++
author = "dev@cyber200"
title = "Network Drivers In Linux"
date = "2024-06-05"
description = "Linux supports a wide variety of Ethernet network interface cards through its extensive collection of network drivers. Each driver is tailored to support specific hardware and provides features suited to different network speeds and capabilities."
tags = [
    "network",
    "hardware",
    "linux",
]
+++

## Overview
These drivers facilitate Ethernet connectivity, managing the transmission and reception of data packets over network connections.Some commonly used network drivers in Linux operating systems, categorized by the type of Ethernet interfaces they manage:

1. Gigabit Ethernet Drivers
    * igb
        * Description: Supports Intel Gigabit Ethernet adapters.
        * Supported Hardware: Intel 82575, 82576, 82580, I210, I211, I350.
        * Features: VLAN support, multiple queue pairs, hardware time stamping, Energy Efficient Ethernet (EEE).
    * e1000e
        * Description: Supports Intel PRO/1000 PCIe network cards.
        * Supported Hardware: Intel 82563, 82566, 82567, 82571, 82572, 82573, 82574, 82583.
        * Features: Advanced interrupt handling, VLAN support, hardware offload features.
    * r8169
        * Description: Supports Realtek Gigabit Ethernet adapters.
        * Supported Hardware: Realtek RTL8168, RTL8111.
        * Features: Basic Gigabit Ethernet functionalities, commonly used in consumer-grade motherboards.
2. 2.5 Gigabit Ethernet Drivers
    * igc
        * Description: Supports Intel 2.5 Gigabit Ethernet adapters.
        * Supported Hardware: Intel I225, I226 series.
        * Features: 2.5 Gigabit speeds, advanced power management, improved performance features.
3. 10 Gigabit Ethernet Drivers
    * ixgbe
       *  Description: Supports Intel 10 Gigabit Ethernet adapters.
        * Supported Hardware: Intel 82598, 82599, X520, X540, X550, X552, X553.
        * Features: 10 Gigabit speeds, multiple queues, SR-IOV support, Data Center Bridging (DCB).
    * sfc
        * Description: Supports Solarflare 10 Gigabit Ethernet adapters.
        * Supported Hardware: Solarflare SFN5xxx, SFN6xxx, SFN7xxx series.
        * Features: High performance, low latency, advanced offloads, and virtualization support.

4. 25/40/50/100 Gigabit Ethernet Drivers
    * mlx5
        * Description: Supports Mellanox 25/40/50/100 Gigabit Ethernet adapters.
        * Supported Hardware: Mellanox ConnectX-4, ConnectX-5, ConnectX-6.
        * Features: High bandwidth, low latency, RDMA over Converged Ethernet (RoCE), SR-IOV.
    * qed
        * Description: Supports QLogic 25/40/50/100 Gigabit Ethernet adapters.
        * Supported Hardware: QLogic QL45xxx series.
        * Features: High throughput, advanced offloads, enhanced virtualization support.
5. Broadcom Ethernet Drivers
    * tg3
        * Description: Supports Broadcom Tigon3 Ethernet adapters.
        * Supported Hardware: Broadcom NetXtreme BCM57xx/BCM59xx.
        * Features: Gigabit Ethernet, VLAN support, multiple transmit/receive queues.
    * bnxt_en
        * Description: Supports Broadcom NetXtreme-C/NetXtreme-E Ethernet adapters.
        * Supported Hardware: Broadcom BCM573xx, BCM574xx, BCM575xx.
        * Features: High performance, 10/25/40/50/100 Gigabit speeds, advanced offloads.
6. Atheros Ethernet Drivers
    * atl1c
        * Description: Supports Atheros AR813x/AR815x Ethernet adapters.
        * Supported Hardware: Atheros AR8131, AR8132, AR8151, AR8152.
        * Features: Basic Ethernet functionality, used in many laptops and consumer-grade motherboards.
    * atlantic
        * Description: Supports Aquantia Multi-Gigabit Ethernet adapters.
        * Supported Hardware: Aquantia AQtion AQC107, AQC108, AQC111.
        * Features: 2.5/5/10 Gigabit speeds, high performance, advanced offloads.
7. Realtek Ethernet Drivers

    * r8168
        * Description: Realtek's own driver for RTL8111/8168 family.
        * Supported Hardware: Realtek RTL8111, RTL8168.
        * Features: Enhanced performance and stability compared to the in-kernel r8169 driver.