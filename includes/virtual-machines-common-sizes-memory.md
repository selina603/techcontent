* Dv2 系列和 D 系列是要求有更快速的 CPU、更好的本地磁盘性能或更高内存的应用程序的理想选择。  它们为许多企业级应用程序提供强大的组合。

D 系列的 VM 旨在运行需要更高计算能力和临时磁盘性能的应用程序。 D 系列 VM 为临时磁盘提供更快的处理器、更高的内存内核比和固态驱动器 (SSD)。 有关详细信息，请参阅 Azure 博客[新的 D 系列虚拟机大小](https://azure.microsoft.com/zh-cn/blog/2014/09/22/new-d-series-virtual-machine-sizes/)上的公告。

Dv2 系列是原 D 系列的后续系列，其特点是 CPU 功能更强大。 Dv2 系列 CPU 比 D 系列 CPU 快大约 35%。 该系列基于最新一代的 2.4 GHz Intel Xeon® E5-2673 v3 (Haswell) 处理器，通过 Intel Turbo Boost Technology 2.0 可以达到 3.1 GHz。 Dv2 系列的内存和磁盘配置与 D 系列相同。

## <a name="dsv2-series"></a>DSv2 系列*

ACU：210-250

| 大小 | CPU 核心数 | 内存：GiB | 本地 SSD：GiB | 最大数据磁盘数 | 缓存磁盘最大吞吐量：IOPS / MBps（以 GiB 为单位的缓存大小） | 非缓存磁盘最大吞吐量：IOPS / MBps | 最大网卡数/网络带宽等级 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Standard_DS11_v2 |2 |14 |28 |4 |8,000 / 64 (72) |6,400 / 96 |2/高 |
| Standard_DS12_v2 |4 |28 |56 |8 |16,000 / 128 (144) |12,800 / 192 |4/高 |
| Standard_DS13_v2 |8 |56 |112 |16 |32,000 / 256 (288) |25,600 / 384 |8/高 |
| Standard_DS14_v2 |16 |112 |224 |32 |64,000 / 512 (576) |51,200 / 768 |8/极高 |
| Standard_DS15_v2*** |20 |140 |280 |40 |80,000 / 640 (720) |64,000 / 960 |8/极高** |

MBps = 每秒 10^6 字节，GiB = 1024^3 字节。

*DSv2 系列 VM 可能的最大磁盘吞吐量（IOPS 或 MBps）可能受限于附加磁盘的数量、大小和条带化。  有关详细信息，请参阅[高级存储：适用于 Azure 虚拟机工作负荷的高性能存储](/documentation/articles/storage-premium-storage/)。

***实例对于专用于单个客户的硬件独立。
<br>
MBps = 每秒 10^6 字节，GiB = 1024^3 字节。

*DS 系列 VM 可能的最大磁盘吞吐量（IOPS 或 MBps）可能受限于附加磁盘的数量、大小和条带化。  有关详细信息，请参阅[高级存储：适用于 Azure 虚拟机工作负荷的高性能存储](/documentation/articles/storage-premium-storage/)。

## <a name="dv2-series"></a>Dv2 系列

ACU：21--250

| 大小              | CPU 核心数 | 内存：GiB | 本地 SSD：GiB | 本地磁盘的最大吞吐量：IOPS/读取 MBps/写入 MBps | 最大的数据磁盘/吞吐量：IOPS | 最大网卡数/网络带宽等级 |
|-------------------|-----------|-------------|----------------|----------------------------------------------------------|-----------------------------------|------------------------------|
| Standard_D11_v2   | 2         | 14          | 100            | 6000/93/46                                           | 4/4x500                         | 2/高                     |
| Standard_D12_v2   | 4         | 28          | 200            | 12000/187/93                                         | 8/8x500                         | 4/高                     |
| Standard_D13_v2   | 8         | 56          | 400            | 24000/375/187                                        | 16/16x500                       | 8/高                     |
| Standard_D14_v2   | 16        | 112         | 800            | 48000/750/375                                        | 32/32x500                       | 8/极高           |
| Standard_D15_v2** | 20        | 140         | 1,000          | 60000/937/468                                        | 40/40x500                       | 8/极高*          |

**实例对于专用于单个客户的硬件来说是独立的。

<br>

## <a name="ds-series"></a>DS 系列*

ACU：160

| 大小 | CPU 核心数 | 内存：GiB | 本地 SSD：GiB | 最大数据磁盘数 | 缓存磁盘最大吞吐量：IOPS / MBps（以 GiB 为单位的缓存大小） | 非缓存磁盘最大吞吐量：IOPS / MBps | 最大网卡数/网络带宽等级 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Standard_DS11 |2 |14 |28 |4 |8,000 / 64 (72) |6,400 / 64 |2/高 |
| Standard_DS12 |4 |28 |56 |8 |16,000 / 128 (144) |12,800 / 128 |4/高 |
| Standard_DS13 |8 |56 |112 |16 |32,000 / 256 (288) |25,600 / 256 |8/高 |
| Standard_DS14 |16 |112 |224 |32 |64,000 / 512 (576) |51,200 / 512 |8/非常高 |

MBps = 每秒 10^6 字节，GiB = 1024^3 字节。

*DS 系列 VM 可能的最大磁盘吞吐量（IOPS 或 MBps）可能受限于附加磁盘的数量、大小和条带化。  有关详细信息，请参阅[高级存储：适用于 Azure 虚拟机工作负荷的高性能存储](/documentation/articles/storage-premium-storage/)。

## <a name="d-series"></a>D 系列

ACU：160

| 大小         | CPU 核心数 | 内存：GiB | 本地 SSD：GiB | 本地磁盘的最大吞吐量：IOPS/读取 MBps/写入 MBps | 最大的数据磁盘/吞吐量：IOPS | 最大网卡数/网络带宽等级 |
|--------------|-----------|-------------|----------------|----------------------------------------------------------|-----------------------------------|------------------------------|
| Standard_D11 | 2         | 14          | 100            | 6000/93/46                                           | 4/4x500                         | 2/高                     |
| Standard_D12 | 4         | 28          | 200            | 12000/187/93                                         | 8/8x500                         | 4/高                     |
| Standard_D13 | 8         | 56          | 400            | 24000/375/187                                        | 16/16x500                       | 8/高                     |
| Standard_D14 | 16        | 112         | 800            | 48000/750/375                                        | 32/32x500                       | 8/非常高                |
<br>

<br>