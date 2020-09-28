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
#include<stdio.h>
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

## 通过外部变量environ访问环境变量
``` C
#include<stdio.h>
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

