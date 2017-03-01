# up command

- 多个 services 是按 service 依赖顺序升级的，先升级依赖项，每个 service 下再按 `--batch-size` 分组；使用 `-d` 可以在所有服务升级后（最后一个 service 所有 containers 进入 Initializing 状态）退出，否则会继续 tail logs
- 使用 `--interval` 参数控制升级时的 batch 间隔：
    - 先 stop 旧的，再 start 新的，interval 是从新 container 进入 Initializing 状态开始计算，不会等到 Running
    - 先 start 新的，再 stop 旧的，interval 是从旧 container 进入 Stopped 状态开始计算
- 使用 `start_fist` 时，会等到新 container 进入 Running 状态再 stop 旧的
- health check 的更改需要 start 一个新 container 后才会生效，并且新旧 containers 都会使用新的配置
- 新 container 进入 Running 只需要通过一次健康检查

# health check

- 会对以下 services 进行检查：
    - 系统：scheduler
    - 所有 rancher lb
    - 所有配置了 `health_check` 的 services
- 多 hosts 会保证跨 host 检查
