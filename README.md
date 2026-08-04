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



## 技术栈

Linux | Shell | Hadoop | HDFS | YARN
