# dynatrace_plugin 简明说明手册
## common pool2控件（V2.1.1）
### 1.jmx监控属性说明
- **FactoryType**: org.apache.commpons.dpcp2/（静态）
- **maxTotal**:允许创建的最大连接对象数量，-1代表不限（静态）
- **maxWaitMillis**:获取资源时的等待时间，单位ms。当blockWhenExhausted 配置为 true时，此值有效。-1代表无时间限制，一直阻塞直到有可用的资源。(静态)
- **maxIdle**：最大空闲资源数，默认8（静态）
- **minIdle**：最小空闲资源数，默认值0（静态）
- **NumActive**:使用资源数（动态）
- **NumIdle**:空闲资源数（动态）
- **NumWaiters**:借出资源数（动态）

## druid pool控件(V1.1.21)
### 1. jmx监控属性说明
一般可以理解为activeCount + poolingCount = maxActive(在限制条件为连接量有最大值时)
- **poolingCount**: 连接池中未使用的连接数
- **activeCount**: 连接池中使用的连接数
- **discardCount**: 验证为无效而被丢弃的连接数
- **destroyCount**:  被关闭的空闲时间超阈值连接 + active运行超过阈值的连接数，默认RemoveAbandoned为false(不处理)即不处理active的连接。
- **Name**: 当前数据源名称 （默认为DataSource-生成ID）

## BoneCP控件(V0.8.0)
### 1. jmx监控属性说明
- **ConnectionWaitTimeAvg**: Return the average time it takes for a getConnection request to be services (in ms).
- **ConnectionsRequested**: Returns the connectionsRequested field.
- **TotalCreatedConnections**: Return total number of connections created in all partitions.
- **TotalFree**: Return the number of free connections available to an application right away (excluding connections that can be created dynamically)
- **TotalLeased**: Return total number of connections currently in use by an application


## HikariCP控件(V2.1.0以上)
***必须RegisterMbeans属性设定为true***
### 1. jmx监控属性说明 com.zaxxer.hikari:type=Pool (HikariPool-0)
- **IdleConnections**: 未使用的连接数
- **ActiveConnections**: 连接池中使用的连接数
- **TotalConnections**: 总有效连接数
- **ThreadsAwaitingConnection**: 线程等待连接数