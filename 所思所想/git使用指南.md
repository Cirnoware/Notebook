> 写在前面：过了一个暑假，居然忘了git要怎么用了（悲），故记录一下，有空的时候看看能不能再系统性的学习一下
## 克隆远程已有仓库：无需先`git init`
1.直接克隆远程仓库（注意挂着代理时可能会出问题，不过不一定）  
    `git clone <链接>`  
此时会在当前目录下生成"xxx(项目名称)"文件夹，其中包含.git文件夹  

- 注意：当克隆github的项目时，可能会报错：  
`fatal: unable to access 'https://github.com/Cirnoware/ZJU-Rule.git/': Failed to connect to github.com port 443 after 21091 ms: Couldn't connect to server`  
这并不是因为操作流程的问题，而是网络的问题（可用gitee验证）

- 说明：本地已有文件时，可能需要先移到别处（不一定，还未试过）

## 远程已有空仓库，初始化并将本地文件上传到远程仓库
```
echo "# Notebook" >> README.md ##可不需要
git init
git add README.md    ## 可改为其他文件
git commit -m "first commit"    ## 可自定义注释
git branch -M main
git remote add origin <https://xxx.github.io>
git push -u origin main
```