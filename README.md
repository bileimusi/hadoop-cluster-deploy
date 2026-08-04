# Hadoop 完全分布式集群搭建

&gt; 基于 Hadoop 3.x，3 节点集群部署实践（NameNode + 2 DataNode）

## 集群架构

| 节点 | IP | 角色 |
|------|-----|------|
| world  | 192.168.21.130 | NameNode / ResourceManager |
| world1 | 192.168.21.131 | DataNode / NodeManager |
| world2 | 192.168.21.132 | DataNode / NodeManager |

## 核心配置

- HDFS：副本数、块大小、NameNode 元数据目录
- YARN：ResourceManager 地址、NodeManager 服务
- 脚本：环境初始化、集群启动、状态检查

## 验证截图

<img width="1908" height="1012" alt="image" src="https://github.com/user-attachments/assets/647de7fb-aafd-42bb-8344-27d7503b0540" />

<img width="1914" height="1027" alt="image" src="https://github.com/user-attachments/assets/e6d588fc-99b5-40e1-9494-e7273c725b27" />

## 集群管理脚本

| 命令 | 作用 | 使用场景 |
|------|------|----------|
| `./scripts/hadoop-cluster.sh start` | 一键启动 HDFS + YARN，并输出各节点进程 | 开机或重启后恢复服务 |
| `./scripts/hadoop-cluster.sh stop` | 一键停止 YARN + HDFS | 维护或关机前 |
| `./scripts/hadoop-cluster.sh status` | 遍历所有节点查看 Java 进程 | 日常巡检、排查故障 |
| `./scripts/hadoop-cluster.sh sync` | 用 rsync 同步配置到所有节点 | 修改配置后分发 |

### 脚本亮点
- **SSH 免密批量管理**：通过循环遍历节点，实现一键查看全集群状态
- **配置一键同步**：基于 rsync 实现配置变更的快速分发，避免手动 SCP
- **集中式启停**：在 NameNode 节点上统一调度，符合生产环境运维规范

#验证截图
<img width="1919" height="1069" alt="image" src="https://github.com/user-attachments/assets/ab30f6b1-c145-4ac6-85a2-8ecfeecb9217" />
<img width="1919" height="861" alt="image" src="https://github.com/user-attachments/assets/c19c60a1-be29-4794-b25e-f654dd4ca3d9" />




## 技术栈

Linux | Shell | Hadoop | HDFS | YARN
