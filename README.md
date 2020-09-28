# LearnNet
## 变元表
``` C
int main(int argc, char *argv[]){
	printf("argc: %d\n", argc);
	printf("argv: %s", argv[0]);
	return 0;
}
```
输出  
argc: 1  
argv: D:\工作\test.exe  

## 环境表
``` C
int main(int argc, char *argv[], char *envp[]){
        int n;
        for(n = 0; envp[n] != (char *)0; ++n){
                printf("%s\n", envp[n]);
        }
        return 0;
}
```
输出：  
一堆环境变量

## 通过外部变量 environ 访问环境变量
``` C
int main(int argc, char *argv[]){
        int n;
        extern char ** environ;
        for(n = 0; environ[n] != (char *)0; ++n){
                printf("%s\n", environ[n]);
        }
        return 0;
}
```
输出：  
一堆环境变量

## 通过 getenv 函数获取特定环境变量的值
``` C
int main(){
        char *str, *getenv();
        if((str = getenv("SHELL")) == (char *)0){
                printf("SHELL is not defined.\n");
        }
        else{
                printf("SHELL = %s.\n", str);
        }
        return 0;
}
```
输出：  
SHELL = /bin/bash.

## 标识符
``` C
int main(){
        printf("进程标识 = %d\n", getpid());
        printf("父进程标识 = %d\n", getppid());
        printf("用户标识符 = %d\n", getuid());
        printf("有效用户标识符 = %d\n", geteuid());
        printf("用户组号 = %d\n", getgid());
        printf("有效用户组号 = %d\n", getegid());
        printf("进程组号 = %d\n", getpgrp());
        return 0;
}
```
输出：  
进程标识 = 14416  
父进程标识 = 13451  
用户标识符 = 0  
有效用户标识符 = 0  
用户组号 = 0  
有效用户组号 = 0  
进程组号 = 14416
## 设置进程组号
`int setpgrp(int pid, int pgrp)` 
pid 为 0 时，该命令作用于当前进程

## Socket()
``` C
#include<sys/types.h>
#include<sys/socket.h>
int socket(int family, int type, int protocol);
//返回一个文件描述符，指通信信道的末端。调用失败返回-1  

// TCP 套接字
int fd0 = socket(AF_INET, SOCK_STREAM, 0);

// UDP 套接字
int fd1 = socket(AF_INET, SOCK_DGRAM, 0);

// 直接访问 IP 的套接字
int fd2 = socket(AF_INET, SOCK_RAW, IPPROTO_RAW);
```

## socketpair()
``` C
#include<sys/types.h>
#include<sys/socket.h>
int socketpair(int family, int type, int protocol, int fd_array[2]);
```
返回两个套接字描述符。调用成功返回2，否则返回-1

``` C
int rc, fd_array[2];

// socketpair() 用 SVR4 面向连接的传输提供者之一产生一个通信信道
rc = socketpair(AF_UNIX, SOCK_STREAM, 0, fd_array);

// socketpair() 用无连接的传输提供者产生一个通信信道
rc = socketpair(AF_UNIX, SOCK_DGRAM, 0, fd_array);
```
