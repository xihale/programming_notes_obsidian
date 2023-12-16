#tool 
## list

```shell
screen -ls
```

## new

>[!question] 换成小写应该没问题 #question

```shell
screen -S [neckname]
screen -R [neckname]
```

>[!note] 使用 `-R` 创建终端
>`-R` 是用来恢复 `screen` 的命令, 当 其 不存在的时候, 则自动创建

## command

`-X`

```shell
screen -R [pid/Name] -X quit
```

