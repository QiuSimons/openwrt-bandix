# OpenWrt-Bandix 网络流量监控工具

[![许可证](https://img.shields.io/badge/许可证-Apache--2.0-blue.svg)](LICENSE)

## 简介

OpenWrt-Bandix 是一个专为 OpenWrt 平台设计的网络流量监控工具。它能够实时监控网络流量，帮助用户了解网络使用情况。

## 功能特点

- 实时监控网络流量
- 低资源占用，适合路由器等嵌入式设备
- 完整的 OpenWrt 集成
- 支持通过 HTTP 获取网络流量统计数据
- 默认监听 br-lan 网口，无需额外配置

## 安装方法

### 从 Release 下载安装

1. 前往 [Release 页面](https://github.com/timsaya/openwrt-bandix/releases) 下载适合您设备架构的 ipk 文件

2. 将下载的 ipk 文件上传到您的 OpenWrt 设备

3. 上传文件到设备并安装：

```bash
opkg install /path/to/bandix_0.1.0-1_xxx.ipk
```

## 使用方法

### 启动服务

```bash
/etc/init.d/bandix start
```

### 设置开机自启

```bash
/etc/init.d/bandix enable
```

### 查看状态

```bash
/etc/init.d/bandix status
```

## API 接口


### 获取设备流量统计

**接口**：`http://<您的路由器IP>:8686/api/devices`

**方法**：GET

**返回示例**：

```json
{
  "devices": [
    {
      "ip": "192.168.1.100",
      "mac": "00:11:22:33:44:55", 
      "rx_bytes": 1024,
      "tx_bytes": 2048,
      "rx_rate": 100,
      "tx_rate": 200
    }
  ]
}
```

**字段说明**：
- `ip`: 设备IP地址
- `mac`: 设备MAC地址
- `rx_bytes`: 设备接收的总字节数
- `tx_bytes`: 设备发送的总字节数
- `rx_rate`: 设备当前接收速率（字节/秒）
- `tx_rate`: 设备当前发送速率（字节/秒）

## 许可证

本项目采用 Apache-2.0 许可证。详情请查看 [LICENSE](LICENSE) 文件。

## 维护者

- [timsaya](https://github.com/timsaya)

## 贡献

欢迎提交问题报告和合并请求！ 