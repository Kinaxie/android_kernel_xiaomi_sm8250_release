# Android Kernel for Xiaomi SM8250 Devices

这是一个针对小米使用高通SM8250平台设备的内核项目。目前支持多款小米设备，但由于某些原因，该内核并未开源。以下是支持的设备列表及其对应的机型名称，以及内核的主要特性概述。

---

## 支持的设备列表

以下是按首字母排列的设备代号及其对应的机型名称：

- **alioth** - Redmi K40 / POCO F3 / Mi 11X  
- **apollo** - Mi 10T / Mi 10T Pro / Redmi K30S Ultra  
- **cas** - Mi 10 Ultra  
- **cmi** - Mi 10 Pro  
- **dagu** - 小米Pad 5 Pro 12.4英寸  
- **elish** - 小米Pad 5 Pro WIFI版  
- **enuma** - 小米Pad 5 Pro 5G版  
- **lmi** - Redmi K30 Pro / POCO F2 Pro  
- **munch** - POCO X3 Pro  
- **pipa** - 小米Pad 6  
- **psyche** - Mi 12X  
- **thyme** - Mi 10S  
- **umi** - Mi 10  

---

## 内核特性概览

### 1. **平台与版本**
   - 专为小米设备定制

### 2. **日志与调试**
   - 增加日志缓冲区大小，支持 PStore 崩溃日志存储和 MTD OOPS 功能。

### 3. **网络与性能优化**
   - 支持 NAT、PEDIT 和 CSUM 分类器操作。
   - 启用 QTI 智能链路聚合驱动（SLA）和高性能日志驱动（XLOGCHAR）。
   - 启用 QCA CLD WLAN 驱动，支持 QCA6390 芯片组。
   - 启用高性能 rmnet 驱动（RMNET_PERF 和 RMNET_SHS）。

### 4. **硬件支持**
   - 支持 AW8697 触觉反馈驱动。
   - 禁用部分未使用的硬件模块（如 MSM_11AD、QTI_MAXIM_FAN_CONTROLLER 等）。

### 5. **文件系统与存储**
   - 支持 EROFS 文件系统。
   - 启用 zRAM 写回功能（ZRAM_WRITEBACK）和 F2FS 文件系统压缩（F2FS_FS_COMPRESSION）。
   - 禁用未使用的 I/O 调度器（如 BFQ、DEADLINE 等）。
   - 优化 zRAM 的 TRIM 操作，减少锁争用和不必要的操作，提升性能。

### 6. **设备树与模块**
   - 支持构建设备树覆盖层（DTBO.img）。
   - 强制加载模块（MODULE_FORCE_LOAD）。

### 7. **MIUI/HyperOS 优化**
   - 支持 MIUI/HyperOS 优化，包括性能关键任务调度、Binder 优化、内存回收（MI Reclaim）等。
   - 启用 ZRAM 内存跟踪和任务调度优化（MIGT、MILLET）。

### 8. **电源与性能优化**
   - 新增低功耗 I/O 参数调整功能，优化脏页比例，减少低功耗模式下的 I/O 活动，提升续航表现。
   - 优化 I/O 性能，减少锁争用和冗余操作，提升整体效率。

### 9. **其他特性**
   - 支持 LCD 类设备（LCD_CLASS_DEVICE）。
   - 设置 SMP2P 睡眠状态时间为 100ms（SMP2P_SLEEPSTATE_TIME）。
   - 启用块设备写回节流（BLK_WBT 和 BLK_WBT_SQ）。
   - ...

---

## 已知问题
   - **umi** 和 **cmi** 设备的相机功能目前存在问题，建议暂时不要使用。

---

## 注意事项
   - 该内核目前未开源，因此无法提供源代码或进行自定义修改。
   - 刷机有风险，请在操作前备份重要数据，并确保了解刷机流程。
   - 如果您发现其他问题或有任何建议，请及时反馈。

---

**免责声明**：本内核仅供学习和研究使用，维护者不对因使用本内核导致的任何问题负责。请谨慎操作。
