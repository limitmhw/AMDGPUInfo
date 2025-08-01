# AMD GPU 型号与 LLVM Target Name 对照表

## 概述
本表格整理了常见 AMD GPU 型号与其对应的 **LLVM target name**（即 `gfx` 架构代号）。LLVM target name 是 AMD GPU 在编译器（如 Clang/LLVM、HIP 编译器）中的核心标识，用于指定编译目标架构，确保内核代码能适配特定 GPU 的硬件特性（如计算单元、指令集等）。

同一架构家族（如 CDNA3、RDNA3）的不同 GPU 型号通常共享相同的 `gfx` 代号，因为它们基于相同的底层架构设计，支持一致的指令集和硬件功能。


## 对照表

| GPU 型号                          | 架构     | LLVM Target Name (gfx 代号) |
|-----------------------------------|----------|------------------------------|
| **AMD Instinct 系列（数据中心级）** |          |                  |
| AMD Instinct MI325X               | CDNA3    | gfx942           |
| AMD Instinct MI300X               | CDNA3    | gfx942           |
| AMD Instinct MI300A               | CDNA3    | gfx942           |
| AMD Instinct MI250X               | CDNA2    | gfx90a           |
| AMD Instinct MI250                | CDNA2    | gfx90a           |
| AMD Instinct MI210                | CDNA2    | gfx90a           |
| AMD Instinct MI100                | CDNA     | gfx908           |
| AMD Instinct MI60                 | GCN5.1   | gfx906           |
| AMD Instinct MI50 (32GB)          | GCN5.1   | gfx906           |
| AMD Instinct MI50 (16GB)          | GCN5.1   | gfx906           |
| AMD Instinct MI25                 | GCN5.0   | gfx900           |
| AMD Instinct MI8                  | GCN3.0   | gfx803           |
| AMD Instinct MI6                  | GCN4.0   | gfx803           |
|                                   |          |                  |
| **AMD Radeon PRO 系列（专业工作站级）** |       |                  |
| AMD Radeon AI PRO R9700           | RDNA4    | gfx1201          |
| AMD Radeon PRO V710               | RDNA3    | gfx1101          |
| AMD Radeon PRO W7900 Dual Slot    | RDNA3    | gfx1100          |
| AMD Radeon PRO W7900              | RDNA3    | gfx1100          |
| AMD Radeon PRO W7800 48GB         | RDNA3    | gfx1100          |
| AMD Radeon PRO W7800              | RDNA3    | gfx1100          |
| AMD Radeon PRO W7700              | RDNA3    | gfx1101          |
| AMD Radeon PRO W6800              | RDNA2    | gfx1030          |
| AMD Radeon PRO W6600              | RDNA2    | gfx1032          |
| AMD Radeon PRO V620               | RDNA2    | gfx1030          |
| AMD Radeon Pro W5500              | RDNA     | gfx1012          |
| AMD Radeon Pro VII                | GCN5.1   | gfx906           |
|                                   |          |                  |
| **AMD Radeon RX 系列（消费级）**   |          |                  |
| AMD Radeon RX 9070 XT             | RDNA4    | gfx1201          |
| AMD Radeon RX 9070 GRE            | RDNA4    | gfx1201          |
| AMD Radeon RX 9070                | RDNA4    | gfx1201          |
| AMD Radeon RX 9060 XT             | RDNA4    | gfx1200          |
| AMD Radeon RX 7900 XTX            | RDNA3    | gfx1100          |
| AMD Radeon RX 7900 XT             | RDNA3    | gfx1100          |
| AMD Radeon RX 7900 GRE            | RDNA3    | gfx1100          |
| AMD Radeon RX 7800 XT             | RDNA3    | gfx1101          |
| AMD Radeon RX 7700 XT             | RDNA3    | gfx1101          |
| AMD Radeon RX 7600                | RDNA3    | gfx1102          |
| AMD Radeon RX 6950 XT             | RDNA2    | gfx1030          |
| AMD Radeon RX 6900 XT             | RDNA2    | gfx1030          |
| AMD Radeon RX 6800 XT             | RDNA2    | gfx1030          |
| AMD Radeon RX 6800                | RDNA2    | gfx1030          |
| AMD Radeon RX 6750 XT             | RDNA2    | gfx1031          |
| AMD Radeon RX 6700 XT             | RDNA2    | gfx1031          |
| AMD Radeon RX 6700                | RDNA2    | gfx1031          |
| AMD Radeon RX 6650 XT             | RDNA2    | gfx1032          |
| AMD Radeon RX 6600 XT             | RDNA2    | gfx1032          |
| AMD Radeon RX 6600                | RDNA2    | gfx1032          |
| AMD Radeon VII                    | GCN5.1   | gfx906           |

## 用途说明
- 在编译 AMD GPU 相关程序（如 HIP 内核、深度学习框架算子）时，需通过 `gfx` 代号指定目标架构（例如通过 `-DGPU_TARGETS=gfx942` 或 `-mllvm --amdgpu-target=gfx942` 等参数）。
- 表格中的 `gfx` 代号可直接用于 CMake 配置、编译器参数或性能优化工具（如 ROCm 生态工具链），确保代码与目标 GPU 硬件特性匹配。
- 若需支持未明确列出的 AMD GPU 型号，可根据其所属架构家族推断对应的 `gfx` 代号（例如 RDNA3 架构通常对应 `gfx1100` 或 `gfx1101`）。
