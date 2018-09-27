
### 1. 预处理
```
#pragma once
```
Remark:
使用#pragma once代替include防範將加快編譯速度，因為這是一種高階的機制；編譯器會自動比對檔案名稱或inode而不需要在標頭檔去判斷#ifndef和#endif。


### 2. 函数
```
_stdcall
```
Microsoft Specific**  
The \__stdcall calling convention is used to call Win32 API functions. 从右向左将参数压入堆栈, 由被调用函数释放堆栈;

```
virtual int getValue() = 0;
```
The curious =0 syntax was chosen ... because at the time I saw no chance of getting a new keyword accepted.

### 3. 多进程编译visual studio
There are two switches that must be set in order to make VS build using multithreading (both are project-specific):

project properties->C/C++->General->Multi-processor Compilation set to: Yes (/MP)
project properties->C/C++->Code Generation->Enable Minimal Rebuild set to: No (/Gm-)
Check also Your Tools->Options->Projects and Solutions->VC++ Project Settings->Maximum concurrent C++ compilations setting. Default value is 0 which enables VS to use as many concurret compilations as possible.
