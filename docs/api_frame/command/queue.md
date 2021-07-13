# `queue`
`queue` 是与消息队列相关的命令集合，包含：
```bash
queue:worker                                      启动队列 worker
queue:status                                      队列状态
queue:pause                                       暂停队列任务派发
queue:peek-buried                                 处理 buried 状态的任务
queue:ready-to-buried                             将 ready 状态的任务快速改变为 buried 状态
queue:buried-dump                                 将 buried 状态的任务快速导出文件并清理
queue:dump-import                                 将导出的 dump 文件快速导入到队列并进入 ready 状态
```
### `queue:worker`
该命令为启动队列 `worker` 的命令，启动后会等待并监听队列，参数 `--tube=xxx` 指定了监听的 `tube`，`--config_key=xxx` 指定了监听的队列的配置，`--memory_limit=xxx` 指定了当完成一次任务后，内存已经超过该值，`worker` 会主动退出，该命令可以起多个进程，开发环境中通过使用 `supervisor` 管理了这个命令的启动数量以及确保该命令进程的存活

### `queue:status`
该命令可以查看队列服务当前的状态，参数 `--tube=xxx` 可以指定所查询的 `tube`，`--config_key=xxx` 指定了查询的队列的配置，如果使用 `beanstalk` 会得到如下的内容：
```php
---
name: default                    // tube 名称
current-jobs-urgent: 0           // 优先级值小于 1024 的任务数量
current-jobs-ready: 0            // 可被领取的任务数量
current-jobs-reserved: 0         // 被领取但没处理完的任务数量
current-jobs-delayed: 0          // 延迟任务的当前数量
current-jobs-buried: 0           // 被挂起的任务数量
total-jobs: 0                    // 总体任务数量
current-using: 6                 // use + watch 这个 tube 的当前连接数，use 通常用于生产者, watch 通常用于消费者
current-watching: 6              // 
current-waiting: 5               // 处于 reserve 状态下等待任务的连接数量
cmd-delete: 0                    // 被删除的任务数量
cmd-pause-tube: 0                // tube 暂停过多少次
pause: 0                         // 此 tube 暂停的秒数
pause-time-left: 0               // 此 tube 暂停剩余的秒数
```

### `queue:peek-buried`
### `queue:ready-to-buried`
### `queue:buried-dump`
### `queue:dump-import`