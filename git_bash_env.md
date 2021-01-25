# git bash环境搭建

首先下载源码。  
安装三连。  
将 `contrib/completion`下的`git-completion.bash`和`git-prompt.sh`拷贝出来，此处以`~/git_scripts`为例。

修改 ~/.bashrc:
```bash
# PS1
source ~/git_scripts/git-completion.bash
source ~/git_scripts/git-prompt.sh
export GIT_PS1_SHOWDIRTYSTATE=1
export GIT_PS1_SHOWSTASHSTATE=1                                               
export GIT_PS1_SHOWUNTRACKEDFILES=1                                           
export GIT_PS1_SHOWUPSTREAM="verbose git svn"
PS1='\[\e[35m\]\t \[\e[32m\]\u \[\e[33m\]\w \[\e[36m\]$(__git_ps1 "<%s>")\[\e[31m\]\n\$ \[\e[0m\]'
```
之后，进入一个git仓库时会自动显示git信息，输入git命令时按<tab>会自动命令提示。
