# websocketd

`websocketd` is a small command-line tool that will wrap an existing command-line interface program, and allow it to be accessed via a WebSocket.

WebSocket-capable applications can now be built very easily. As long as you can write an executable program that reads `STDIN` and writes to `STDOUT`, you can build a WebSocket server. Do it in Python, Ruby, Perl, Bash, .NET, C, Go, PHP, Java, Clojure, Scala, Groovy, Expect, Awk, VBScript, Haskell, Lua, R, whatever! No networking libraries necessary.



# websocketd的下载地址

https://github.com/joewalnes/websocketd/releases



## 创建一个将数据输出到STDOUT的程序

**count.sh**:

```
#!/bin/bash

# Count from 1 to 10, pausing for a second between each iteration.
for COUNT in $(seq 1 10); do
  echo $COUNT
  sleep 1
done
```

使它可执行：

```
$ chmod +x ./count.sh
```

## 启动websocketd服务器

```
$ websocketd --port=8080 ./count.sh
```

## 使用JavaScript连接到您的WebSocket

在网页中：

```
var ws = new WebSocket('ws://localhost:8080/');
    
ws.onmessage = function(event) {
  console.log('Count is: ' + event.data);
};
```