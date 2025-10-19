## shell笔记

1. 新建一个文件

   `vi hello.sh`

2. 文件内容

   ``` shell
   #!/bin/bash
   
   echo "hello shell"
   date
   whoami
   ```

3.  执行

   `chmod a+x hello.sh`给文件添加执行权限

   `./hello.sh`

#### shell脚本示例

```shell
#!/bin/bash
echo "请输入您的姓名："
read name
echo "您好，$name"
```

`./game.sh`需要给这个文件添加一个执行权限`chmod +x game.sh`

或`bash game.sh`

#### 传递参数

```shell
#!/bin/bash
echo "请输入您的姓名："
name=$1
channel=$2
echo "您好，$name,欢迎来到$channel"
```

`./game.sh 小明 geekhour`

#### 环境变量

`export`定义环境变量，该变量在脚本中也能访问，但退出终端后再打开终端则此变量丢失

`export name=小明`

#### 环境变量永久有效

shell启动时会读取一些配置文件，一般把环境变量放到.bashrc文件中

`nano .bashrc`打开文件，在文件最后使用export添加变量

修改.bashrc文件后，需要使用`source .bashrc`重新读取配置文件

#### 猜数字游戏

> Linux命令：`shuf -i 1-10 -n 1`,表示生成随机数范围1到10数量1个

```shell
#!/bin/bash
number=`shuf -i 1-10 -n 1`  
number=$(shuf -i 1-10 -n 1) 
echo $number
echo "请输入一个1到10的数字"
read guess
if [[$guess -eq $number]];then
	echo "猜对了"
fi
```

```shell
#!/bin/bash
number=`shuf -i 1-10 -n 1`  
number=$(shuf -i 1-10 -n 1) 
echo $number
echo "请输入一个1到10的数字"
read guess
if [[$guess -eq $number]];then
	echo "猜对了"
else 
	echo "猜错了"
fi
```

```shell
#!/bin/bash
number=`shuf -i 1-10 -n 1`  
number=$(shuf -i 1-10 -n 1) 
echo $number
while [[$guess -ne $number]]
do
echo "请输入一个1到10的数字"
read guess
if [[$guess -eq $number]];then
	echo "猜对了"
elif [[$guess -lt $number]];then
	echo "小了"
else 
	echo "大了"
fi
done
```

```shell
#!/bin/bash
number=`shuf -i 1-10 -n 1`  
number=$(shuf -i 1-10 -n 1) 
echo $number
while true
do
echo "请输入一个1到10的数字"
read guess
if [[ $guess -eq $number ]];then
	echo "恭喜你猜对了!是否继续?(y/n):"
	read choice
	if [[ $choice = "y" ]] || [[ $choice = "Y" ]];then
		number=$((RANDOM % 10 + 1))
		echo $number
		continue
	else
		break
	fi
elif [[ $guess -lt $number ]];then
	echo "小了"
else 
	echo "大了"
fi
done
```

`echo $RANDOM`生成随机数0-32767

`echo $((RANDOM % 10))`生成0-9随机数

`echo $((RANDOM % 10 +1))`生成1-10随机数

#### 注意点

- 若你使用的是 `/bin/sh`（非 bash），则不能使用 `[[ ]]`，必须改为 `[ ]` 并注意语法。

```shell
if [[$guess -eq $number]];then   # ❌ 错误
if [[ $guess -eq $number ]]; then # ✅ 正确

if [[$choice ="y"]]              # ❌ 错误
if [[ $choice = "y" ]]           # ✅ 正确
```

