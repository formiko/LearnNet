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
int main(int argc, char *argv[]){
        int n;
        extern char ** environ;
        for(n = 0; environ[n] != (char *)0; ++n){
                printf("%s\n", environ[n]);
        }
        return 0;
}
```
