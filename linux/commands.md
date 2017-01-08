Linux common commands tips
========================

#### 1: 当某个端口被占用时怎么kill掉占用该端口的进程？
  首先找到该进程的 PID；然后 kill PID。
  * `$ lsof -wni tcp:3000`
  * `$ kill -9 PID`

------------------
