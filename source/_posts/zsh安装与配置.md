---
title: zsh安装与配置
date: 2023-11-11 16:02:57
tags:
---
# zsh安装与配置

## 安装 zsh

~~~shell
#Ubuntu
sudo apt install zsh -y
~~~

安装完成后使用 `cat /etc/shells` 查看系统中可以用的 shell

<img src="https://cdn.jsdelivr.net/gh/olyw/PicGo/images/2023/image-20230217173821568.png" alt="image-20230217173821568" style="zoom:67%;" />

使用 `chsh -s /bin/zsh` 命令将 zsh设置为系统默认 shell，然后新开一个 session就可以开始使用 zsh。第一次运行 zsh时会有引导配置界面，输入 `q` 退出配置引导。

<img src="https://cdn.jsdelivr.net/gh/olyw/PicGo/images/2023/image-20230808194340009.png" alt="image-20230808194340009" style="zoom:50%;" />

## 安装 oh-my-zsh

使用 curl 下载脚本并运行安装脚本

~~~shell
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
~~~

## 配置 zsh

配置文件 `~/.zshrc`

### 修改主题

#### 安装主题

选择使用 `powerlevel10k`主题

使用 git 将主题 clone 到本地的 `.oh-my-zsh/custom/themes `目录

~~~shell
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
~~~

编辑配置文件中主题设置部分并保存，执行`source ~/.zshrc` 命令生效修改后的配置

~~~shell
ZSH_THEME="powerlevel10k/powerlevel10k"
~~~

### 安装插件

把插件下载到本地的 `~/.oh-my-zsh/custom/plugins` 目录

* **z** ：文件夹快捷跳转插件（oh-my-zsh 内置）

* **zsh-autosuggestions**：命令提示插件

    ~~~shell
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
    ~~~

* **zsh-syntax-highlighting**：命令语法校验插件

    ~~~shell
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting 
    ~~~

    编辑配置文件中插件设置部分并保存，执行`source ~/.zshrc` 命令生效修改后的配置

~~~shell
plugins=(
    # other plugins...
    z
    zsh-autosuggestions
    zsh-syntax-highlighting
)
~~~