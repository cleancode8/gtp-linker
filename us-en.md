[简体中文](https://github.com/ZhuRongJian/gtp-linker) | English

## Competition Notes for 2020 Fuzhou World AI Go Provisions 

#### Please ensure your AI connector version is the latest, it's v2.2.

### 1 GTP connector download and instructions for use

> https://github.com/ZhuRongJian/gtp-linker/releases

> 4 files included in the resource：

```
config.yaml             // The configuration file for the linker
gtp-linker_linux        // Linux client
gtp-linker_mac          // OSX client
gtp-linker_windows.exe  // Windows client
```

### 2 Explanation for the config file

```
game:
  kgs_time: "Y"   // is or not output kgs-time_setting
  safe_time: "3"  // safe time(s)，will be reduced in time_left
  shell: ""       // AI Engine 
lang: "cn"        // language setting
user:
  account: ""     // login account
  password: ""    // login password
```

### 3 Explanation for the commands

```
./gtp-linker_[os] config  // mofify config.yaml via command
./gtp-linker_[os] ping    // network latency check
./gtp-linker_[os] debug   // go into debug mode, invite another player
./gtp-linker_[os] run     // waiting mode, automaticly find games to start
```

#### 3.1 config

> You can modify the settings as follows

1. Use the command line tool to enter the following words， and operate according to the feedback.

```
> cd  "linker dir"
> ./gtp-linker_[os] config
```

2. Manually modify the `config.yaml` file and save.

#### 3.2 ping

> This command is used to check the network latency between the client and the server.

Use the command line tool to enter the following words， and operate according to the feedback.

```
> cd  "linker dir"
> ./gtp-linker_[os] ping
```

#### 3.3 debug

> This command is only used before competition.
> 
> 1. used by inviter, game creator

Use the command line tool to enter the following words， and operate according to the feedback.

```
> cd  "linker dir"
> ./gtp-linker_[os] debug
```

#### 3.4 run

> This command is used before competition and in competition.
>
> 1. before competition，used by acceptor，waiting for the inviter to create game.
> 2. in competition，waiting for the referee to pair games.

Use the command line tool to enter the following words， and operate according to the feedback.

```
> cd  "linker dir"
> ./gtp-linker_[os] run
```

### 4 Specific Notes

#### 4.1 Commands used by the GTP Linker

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

#### 4.2 About config key safe_time

> safe_time, optional

1. if your engine has its time strategy(network latency、calculation offset of engine)，keep it as "0".
2. if not, please config it carefully.

#### 4.3 About config key kgs_time

> kgs_time, optional

1. when the value is "Y"，GTP Linker will output `kgs-time_settings byoyomi x y z` to the enginee.
2. x means the left main time，y means the left byoyomi time，z means the left byoyomi times.
3. if your engine doesn't support this output, please keep it as "N".
 
#### 4.4 About continuously reconnect in abnormal connection connection

1. If abnormal network connection occured, GTP Linker will continuously reconnect until succeed.
2. You need to pay close attention to the status of GTP Linker. 

#### 4.5 About arbitration

> In the final stage, arbitration apply needs following logs.

1. log file of engine，you need open it in the config file of AI Engine.
2. log file of GTP Linker，it will automaticly generated in the log folder of the root，you can change the file name via following command.

```
./gtp-linker_[os] -l xx.log run/debug
```
