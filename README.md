# Raspberry Pi 4 Model B Performance Benchmarks

# Raspberry Pi Specification

* Broadcom BCM2711 SoC
* 1.5GHz Clock
* 4 x Arm Cortex-A72 cores, 64-bit armv8.0-a architecture
* 1 x 128 bit SIMD pipeline per core, capable of 2 x double precision FMA operations per clock cycle
* 4GB RAM

# Baseline High Performance Linpack (HPL) Benchmarks

HPL benchmarks Ubuntu 20.04 LTS 64-bit Pre-Installed Server default packages:

* OpenBLAS (serial) 0.3.8
* BLIS (serial) 0.6.1
* OpenMPI 4.0.3

HPL-2.3 built from source with ```-O3 -march=armv8-a -mtune=cortex-a72```

The theoretical maximum performance for a single node:

```
Rpeak = 1.5GHz clock * 4 cores * 4 floating point operations per clock cycle
Rpeak = 24 Gflops
```

Using 80% of memory results in a maximum achievable:

```
80% Rpeak = 19.2 Gflops per node
80% Rpeak =  4.8 Gflops per core
```

## Gflops vs NB 1 Core 80% Memory
![](plots/gflops_vs_nb_1_core_80_percent_memory.png)

## Gflops vs NB 1 Node (4 Cores) 80% Memory
![](plots/gflops_vs_nb_1_node_80_percent_memory.png)

## Gflops vs NB 2 Nodes 80% Memory
![](plots/gflops_vs_nb_2_node_80_percent_memory.png)

## Gflops vs Nodes 80% Memory

Rmax is the maximum observed Gflops using the following values of NB:

* OpenBLAS NB = 120 
* BLIS     NB = 168

These values are the NB which achieved Rmax for the 2 node benchmark. The assumption that this extrapolates to the 8 node benchmark  neeeds further investigation.

![](plots/gflops_vs_nodes_80_percent_memory.png)

