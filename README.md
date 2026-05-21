# LFGateway — 高性能 API 网关



## 项目概述
LFGateway 是一个基于自研 **Reactor 网络框架** 的高性能企业级 API 网关，支持 **MySQL/Redis 连接池、鉴权、限流、路由管理与异步日志**。  

项目目标是提供 **低延迟、高并发** 的 API 请求处理能力，适合大型分布式服务场景。

- 独立开发，完整从零实现  
- 支持万级并发连接，稳定高效  
- 学习底层网络编程和高性能后端开发的优秀案例  

---

## 功能特性
- **网络框架**
  - 基于 **epoll + Reactor** 的非阻塞 I/O 模型  
  - 封装 `EventLoop` / `Channel` / `TcpConnection`  
  - 支持 Keep-Alive 长连接  
- **业务链路**
  - 插件式鉴权模块（Redis 缓存 token）  
  - 限流模块（Redis INCR 固定窗口）  
  - 动态路由管理，结合 MySQL 完整处理 API 请求  
- **异步日志**
  - 生产者-消费者模式批量写入 MySQL  
  - 避免业务线程阻塞，日志吞吐量可达 **10,000 条/秒**  
- **运维能力**
  - 自定义端口管理与文本协议  
  - 实时 QPS/延迟统计  
  - 动态路由下发，方便运维监控  
- **性能指标**
  - `wrk` 压测：QPS **56,000+**  
  - 平均延迟：**1.98ms**  
  - 5000+ 并发连接稳定运行  

---

## 技术栈
- **语言**：C++11/14/17  
- **操作系统**：Linux  
- **网络编程**：Socket、TCP/IP、HTTP/1.1、Reactor 模型  
- **数据库**：MySQL（索引/SQL 优化）  
- **缓存**：Redis（缓存策略/原子计数器）  
- **工具**：Git、CMake、GDB、wrk  

---

## 安装与运行
1. 克隆项目：
   ```bash
   git clone https://github.com/whn121/LFGateway.git
   cd LFGateway
````

2. 编译：

   ```bash
   mkdir build && cd build
   cmake ..
   make -j
   ```
3. 配置数据库：

   * 修改 `config/mysql_config.json` 填写 MySQL 与 Redis 连接信息
4. 启动网关：

   ```bash
   ./LFGateway
   ```
5. 查看日志与性能：

   * 日志存储在 MySQL
   * 可通过自定义管理端口获取实时 QPS 与延迟数据

## 项目结构

LFGateway/
├─ src/               # 核心源代码（Reactor框架、业务逻辑）
├─ include/           # 头文件
├─ config/            # 配置文件（数据库、路由等）
├─ scripts/           # 启动/测试脚本
├─ docs/              # 项目文档
└─ build/             # 编译输出

## 联系方式

* 作者：王浩楠
* 邮箱：[2408679829@qq.com](mailto:2408679829@qq.com)
* GitHub：[github.com/whn121](https://github.com/whn121)

