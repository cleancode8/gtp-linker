简体中文 | [English](https://github.com/ZhuRongJian/gtp-linker/blob/master/us-en.md)

## 2020福州世界人工智能赛-AI连接器使用文档

#### 请确保您的连接器为大会最新版本，当前版本v2.2。

### 一 下载连接器和文件解释

> https://github.com/ZhuRongJian/gtp-linker/releases

> 在资源包中有4个文件分别为：

```
config.yaml             // 连接器的配置文件
gtp-linker_linux        // Linux客户端
gtp-linker_mac          // osx客户端
gtp-linker_windows.exe  // Windows客户端
```

### 二 配置文件详解

```
game:
  kgs_time: "Y"   // 是否输出 kgs-time_setting
  safe_time: "3"  // 安全时间(秒)，会在 time_left 中自动扣减
  shell: ""       // AI Engine 启动命令文件
lang: "cn"        // GTP Linker 输出文字的语言，支持 cn / en
user:
  account: ""     // 登录名，由主办方提供
  password: ""    // 登录密码，由主办方提供
```

### 三 指令一览及说明

```
./gtp-linker_[os] config  // 通过命令行修改 config.yaml 文件
./gtp-linker_[os] ping    // 网络连接测速
./gtp-linker_[os] debug   // 邀请方式调式对局
./gtp-linker_[os] run     // 自动寻找对局，自动开始(如有多盘，需要手工选择确认)
```

#### 3.1 config

> 您可使用如下方式修改配置内容

1. 使用命令行工具输入如下内容，并根据提示进行操作。

```
> cd  "linker dir"
> ./gtp-linker_[os] config
```

2. 手工修改 `config.yaml` 文件并保存。

#### 3.2 ping

> 此命令用于检查客户端与服务器之前的网络延迟情况。

使用命令行工具输入如下内容，并根据提示进行操作。

```
> cd  "linker dir"
> ./gtp-linker_[os] ping
```

#### 3.3 debug

> 此命令仅用于赛前调试。
> 
> 1. 邀请方使用，输入对方的登录账号即可发起对局邀请。

使用命令行工具输入如下内容，并根据提示进行操作。

```
> cd  "linker dir"
> ./gtp-linker_[os] debug
```

#### 3.4 run

> 此命令用于赛前调试以及正赛。
>
> 1. 赛前调试，被邀请方使用，等待对方创建对局，自动开始
> 2. 正赛，等待裁判编排对局，自动开始

使用命令行工具输入如下内容，并根据提示进行操作。

```
> cd  "linker dir"
> ./gtp-linker_[os] run
```

### 四 特殊说明

#### 4.1 GTP Linker 使用到的引擎命令有

```
clear_board
boardsize
time_settings
komi
play
gen_move
time_left
kgs-time_settings
```

#### 4.2 关于配置 safe_time 的使用

> safe_time，可选参数。

1. 如果引擎有时间策略(网络延迟、引擎计算误差)的考虑，建议设置为 0 。
2. 如果没有，请选手根据实际情况谨慎设置。

#### 4.3 关于配置 kgs_time 的使用

> kgs_time，可选参数。

1. 开启后，GTP Linker 会输出 `kgs-time_settings byoyomi x y z` 给引擎。
2. 其中 x 代表剩余常规时间，y 代表剩余读秒时间，z 代表剩余读秒次数。
3. 如果选手引擎不支持此命令的输出，建议选手谨慎设置，以防不识别而导致的引擎异常。
 
#### 4.4 网络波动或异常后的重连机制的说明

1. 当选手在比赛时出现网络波动或异常后，GTP Linker 会持续保持重连服务器，直到成功为止。
2. 选手应在比赛中持续关注 GTP Linker 的状态，如需手工干预，自行退出程序。

#### 4.5 关于申诉流程的补充说明

> 在决赛阶段，申诉的选手必须提供如下内容：

1. 引擎日志，参赛选手自行在引擎中开启
2. 连接器日志，GTP Linker 会自动在程序根目录log文件夹中生成，选手也可通过如下方式修改日志文件名。

```
./gtp-linker_[os] -l xx.log run/debug
```
