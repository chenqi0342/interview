#
## 1 commander: 解析参数 —help
##   .command('xxx') //command用户输入
##   .description('xxxx)//描述
##   .option('-g, --get <path>', 'get value from option')//选项
##   .option('-s, --set <path> <value>') //选项
##   .option('-d, --delete <path>', 'delete option from config') //选项
##   .action((value, cmd) => { console.log(value, cmd) }) //提取cmd中的属性

## //解析用户执行命令传入的参数
## 命令行交互的功能 inquirer
## 将模版下载下来 download-git-rpeo

## 2 inquirer: 交互式命令行工作，实现命令行的选择功能
## 3 download-git-repo: 在git中下载模版
## 4 chalk粉笔
## node把可执行的文件都放在一个目录下bin目录
##   #! /usr/bin/env node 

