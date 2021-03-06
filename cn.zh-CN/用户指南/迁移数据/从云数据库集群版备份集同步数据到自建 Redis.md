# 从云数据库集群版备份集同步数据到自建 Redis {#concept_np4_myf_vdb .concept}

## 从控制台下载备份集数据 { .section}

1.  登录[Redis 管理控制台](https://kvstore.console.aliyun.com/)，定位目标实例。
2.  单击实例 ID 或者**管理**进入实例信息页面。
3.  在实例架构图中查看 db 节点个数。
4.  在备份与恢复页面，根据 db 节点个数下载备份集数据。

## 下载 redis-port { .section}

[redis-port地址](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/66008/cn_zh/1526545851725/redis-port)

## 使用示例 { .section}

```
./redis-port  restore  --input=x/dump.rdb  --target=dst\_host:dst\_port   --auth=dst\_password  [--filterkey="str1|str2|str3"] [--targetdb=DB] [--rewrite] [--bigkeysize=SIZE] [--logfile=REDISPORT.LOG]
```

**说明：** 

需要将每个 db 的备份集执行一遍恢复程序。

**参数说明**

-   x/dump.rdb：云数据库 redis 备份集的 dump 文件路径
-   dst\_host：自建 redis 域名（或者 IP）
-   dst\_port：自建 redis 端口
-   dst\_password：自建 redis 密码
-   str1|str2|str3：过滤具有 str1 或 str2 或 str3 的 key
-   DB：将同步入自建 redis 的 DB
-   rewrite：覆盖已经写入的 key
-   bigkeysize=SIZE：当写入的 value 大于 SIZE 时，走大 key 写入模式

## 根据 redis-port 日志查看数据恢复状态 { .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3153/2663_zh-CN.png)

当出现`restore: rdb done`时数据恢复完成。

