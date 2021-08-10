# linux 查询命令的方式

## 1. type

### 语法

```bash
$ type [-tpa] name
```

**选项与参数:**

不加任何选项与参数时，`type` 会显示 `name` 是外部命令还是 bash 的内置命令

+ **`-t`** 将会打印如下 3 种情况：
  + file: `name` 是外部指令
  + alias: `name` 是命令别名
  + builtin: `name` 是 bash 的内置命令
+ **`-p`** 若 `name` 是外部命令，将会显示完整的文件名
+ **`-a`** 把 PATH 变量定义的路径中所有含 `name` 的命令都列出来，包括 alias

### 例子

1. 查询 ls 是否为 bash 内置命令

```bash
root@www:~$ type ls
ls 是“ls --color=auto”的别名

root@www:~$ type -t ls
alias

root@www:~$ type -a ls
ls 是“ls --color=auto”的别名
ls 是 /usr/bin/ls              <== 找到有外部指令在 /usr/bin/ls
ls 是 /bin/ls                  <== 找到有外部指令在 bin/ls
```

2. 查询 cd 是否为 bash 内置命令

```bash
root@www:~$ type cd
cd 是 shell 内建
```

## 2. which

### 语法

```bash
$ which [-a] command
```

**选项与参数:**

+ **`-a`** 把 PATH 变量定义的路径中所有含 `name` 的命令都列出来

### 例子

1. 查找 ifconfig 的完整文件名

```bash
root@www:~$ which ifconfig
/usr/sbin/ifconfig
```

2. 用 which 去找出 which 的文件名

```bash
root@www:~$ which which
/usr/bin/which
```

3. 用 which 去找 history 的完整文件名

```bash
root@www:~$ which history
# 不打印任何结果
```

history 是 bash 的内置命令，但 which 只找 PATH 内所设置的目录，所以是找不到的。可以用 type 命令来查找。

