STP Triangle Topology
Objective:
In this project, we configure a basic **Spanning Tree Protocol (STP)** in a **triangle topology** to understand loop prevention and port roles. This example uses **3 switches** arranged in a triangle to illustrate how STP works to prevent network loops and ensure redundancy.
---
Devices Used:
- **Switches**: 3 (SW1, SW2, SW3)
- **Connections**:  
  - SW1 ↔ SW2 (via Fa0/1)  
  - SW2 ↔ SW3 (via Fa0/2)  
  - SW3 ↔ SW1 (via Fa0/2)
  Steps:
Step 1: Basic Switch Setup (Hostnames)
We start by naming the switches to make identification easier.
S witch> enable
Switch# config terminal
Switch(config)# hostname SW1
# Repeat for SW2 and SW3
SW1(config)# spanning-tree vlan 1 priority 0
SW2(config)# spanning-tree vlan 1 priority 4096
SW3(config)# spanning-tree vlan 1 priority 8192
Step 3: Connect the Switches
Use crossover cables to connect the switches as shown:

SW1 → Fa0/1 → SW2

SW2 → Fa0/2 → SW3

SW3 → Fa0/2 → SW1

This creates a triangle (loop), which STP will handle.
Step 4: Enable STP (By default, STP is enabled)
SW1# show spanning-tree

Step 6: Observe the Port Roles
Root Port (RP): The port on a switch that points toward the Root Bridge.

Designated Port (DP): The port selected to forward traffic on a given network segment.

Alternate Port (ALTN): This port is blocked to prevent a loop in the network.

We Learned:
Root Bridge: SW1 becomes the Root Bridge due to the lowest priority.

Loop Prevention: STP blocks the redundant path between SW3 and SW1 to prevent loops.

Port Roles: Ports are assigned Root, Designated, and Blocking roles based on the STP election process.
