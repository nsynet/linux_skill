[TOC]

# Docker 常用命令快速参考卡片 📦

***

#### **容器生命周期管理**

| 命令                             | 说明                    |
| :----------------------------- | :-------------------- |
| `docker run [选项] 镜像`           | 创建并启动容器               |
| `docker start/stop/restart 容器` | 启动/停止/重启容器            |
| `docker rm 容器`                 | 删除容器（`-f` 强制删除运行中的容器） |
| `docker pause/unpause 容器`      | 暂停/恢复容器进程             |
| `docker update 容器`             | 更新容器的资源限制（如 CPU/内存）   |

**常用 `run`**\*\* 选项\*\*：

*   `-d` 后台运行
*   `--name 名称` 指定容器名称
*   `-p 宿主机端口:容器端口` 端口映射
*   `-v 宿主机路径:容器路径` 挂载数据卷
*   `-e 变量=值` 设置环境变量
*   `--network 网络` 指定容器网络
*   `-it` 启动交互式终端（通常与 `/bin/bash` 结合）

***

#### **容器操作**

| 命令                       | 说明                                       |
| :----------------------- | :--------------------------------------- |
| `docker ps`              | 查看运行中的容器（`-a` 显示所有）                      |
| `docker logs 容器`         | 查看日志（`-f` 实时跟踪）                          |
| `docker exec [选项] 容器 命令` | 在容器内执行命令（如 `-it /bin/bash` 进入终端）         |
| `docker inspect 容器`      | 查看容器详细信息（JSON 格式）                        |
| `docker stats`           | 实时监控容器资源使用（CPU/内存）                       |
| `docker cp 容器:路径 宿主机路径`  | 从容器复制文件到宿主机（反向同理）                        |
| docker stop <容器名或容器ID>   | 向容器发送 `SIGTERM` 信号，允许容器优雅终止（保存数据、清理资源）   |
| docker kill <容器名或容器ID>   | 直接向容器发送 `SIGKILL` 信号，立即终止容器进程（适用于无响应的情况） |
| docker rm -f <容器名或容器ID>  | 彻底清理容器（停止并删除）                            |
|                          |                                          |

***

#### **镜像管理**

| 命令                          | 说明                          |
| :-------------------------- | :-------------------------- |
| `docker images`             | 列出本地镜像                      |
| `docker rmi 镜像`             | 删除镜像（`-f` 强制删除）             |
| `docker pull 镜像:标签`         | 拉取镜像（默认标签 `latest`）         |
| `docker push 镜像:标签`         | 推送镜像到仓库                     |
| `docker build -t 名称:标签 路径`  | 构建镜像（`-f` 指定 Dockerfile 路径） |
| `docker tag 旧镜像 新镜像:标签`     | 为镜像打标签                      |
| `docker save -o 文件名.tar 镜像` | 导出镜像为文件                     |
| `docker load -i 文件名.tar`    | 从文件导入镜像                     |

***

#### **网络管理**

| 命令                                | 说明         |
| :-------------------------------- | :--------- |
| `docker network ls`               | 列出所有网络     |
| `docker network create 网络名`       | 创建自定义网络    |
| `docker network inspect 网络`       | 查看网络详细信息   |
| `docker network connect 网络 容器`    | 将容器连接到网络   |
| `docker network disconnect 网络 容器` | 断开容器与网络的连接 |

***

#### **数据卷管理**

| 命令                         | 说明      |
| :------------------------- | :------ |
| `docker volume create 卷名`  | 创建数据卷   |
| `docker volume ls`         | 列出所有数据卷 |
| `docker volume inspect 卷名` | 查看卷详细信息 |
| `docker volume rm 卷名`      | 删除数据卷   |

***

#### **其他实用命令**

| 命令                    | 说明                   |
| :-------------------- | :------------------- |
| `docker version`      | 查看 Docker 版本         |
| `docker info`         | 显示 Docker 系统信息       |
| `docker login`        | 登录镜像仓库（如 Docker Hub） |
| `docker search 关键词`   | 搜索镜像仓库               |
| `docker system df`    | 查看 Docker 磁盘使用       |
| `docker system prune` | 清理无用数据（镜像/容器/网络/缓存）  |

***

**小贴士**：

*   使用 `--help` 查看命令帮助（如 `docker run --help`）。
*   组合命令示例：`docker run -d --name web -p 80:80 -v /data:/app nginx:alpine`

保存这张卡片，快速查阅 Docker 核心命令！

# WSL (Windows Subsystem for Linux) 常用命令快速参考卡片 🐧🔧

***

#### **生命周期管理**

| 命令                       | 说明                   |
| :----------------------- | :------------------- |
| `wsl --install`          | 安装 WSL（默认安装 Ubuntu）  |
| `wsl --shutdown`         | 强制关闭所有 WSL 发行版和虚拟机   |
| `wsl --terminate <发行版名>` | 终止指定发行版              |
| `wsl --status`           | 查看 WSL 状态（版本、默认发行版等） |

***

#### **发行版管理**

| 命令                                 | 说明                     |
| :--------------------------------- | :--------------------- |
| `wsl --list` 或 `wsl -l`            | 列出已安装的发行版（`-v` 显示详细信息） |
| `wsl --set-default <发行版名>`         | 设置默认启动的发行版             |
| `wsl --set-version <发行版名> 2`       | 将发行版升级到 WSL 2          |
| `wsl --unregister <发行版名>`          | 注销并删除发行版（删除数据）         |
| `wsl --export <发行版名> 文件名.tar`      | 导出发行版为备份文件             |
| `wsl --import <发行版名> 安装路径 文件名.tar` | 从备份文件导入发行版             |

***

#### **配置管理**

| 命令              | 说明                                |
| :-------------- | :-------------------------------- |
| `wsl --update`  | 更新 WSL 内核                         |
| `wsl --version` | 查看 WSL 版本信息                       |
| `wsl -d <发行版名>` | 启动指定发行版（例如 `wsl -d Ubuntu-22.04`） |
| `wsl.conf` 配置文件 | 路径：`/etc/wsl.conf`（用于配置默认用户、网络等）  |

***

#### **文件系统交互**

| 命令                | 说明                                        |
| :---------------- | :---------------------------------------- |
| `\\wsl$\<发行版名>`   | 在 Windows 资源管理器中访问 WSL 文件系统               |
| `wsl --cd <目录>`   | 在 WSL 中直接切换到指定目录（Windows 路径自动转换）          |
| `wsl <Windows命令>` | 从 WSL 中调用 Windows 命令（如 `wsl calc` 打开计算器）  |
| `<Linux命令>`       | 从 Windows 命令行直接运行 Linux 命令（如 `wsl ls -l`） |

***

#### **网络与性能**

| 命令/配置                       | 说明                                               |
| :-------------------------- | :----------------------------------------------- |
| `ip addr show eth0`         | 查看 WSL 2 的 IP 地址（默认 NAT 网络）                      |
| `wsl.conf` 中的 `[network]`   | 配置 DNS、生成 hosts 文件等                              |
| `localhost`                 | 在 Windows 中通过 `localhost` 访问 WSL 服务（WSL 2 需端口转发） |
| `netsh interface portproxy` | Windows 端口转发命令（用于 WSL 2 网络访问）                    |

***

#### **备份与恢复**

| 命令    | 示例                                                           |
| :---- | :----------------------------------------------------------- |
| 导出发行版 | `wsl --export Ubuntu-22.04 ubuntu_backup.tar`                |
| 导入发行版 | `wsl --import NewUbuntu C:\wsl\new_ubuntu ubuntu_backup.tar` |
| 备份根目录 | `tar -zcvf wsl_backup.tar.gz /`（在 WSL 中执行）                   |

***

#### **实用技巧**

1.  **快速启动默认发行版**：直接运行 `wsl` 或 `bash`（需默认配置）。
2.  **切换默认用户**：

    1.  `echo -e "[user]\ndefault=新用户名" | sudo tee /etc/wsl.conf`
3.  **限制 WSL 2 内存/CPU**：在 `%USERPROFILE%\.wslconfig` 中添加：

    1.  `[wsl2] memory=4GB # 限制内存 processors=2 # 限制 CPU 核心`
4.  **关闭 WSL 虚拟机**：`wsl --shutdown`（释放资源）。

***

**小贴士**：

*   使用 `wsl --help` 查看完整命令帮助。
*   WSL 1 和 WSL 2 的区别：

    *   **WSL 1**：轻量级兼容层，直接翻译 Linux 系统调用。
    *   **WSL 2**：基于 Hyper-V 的完整 Linux 内核，性能更高（推荐用于 Docker 等场景）。

保存这张卡片，轻松管理你的 Windows + Linux 混合开发环境！

# Git 常用命令快速参考卡片

***

#### **基础配置**

| 命令                                    | 说明      |
| :------------------------------------ | :------ |
| `git config --global user.name "名字"`  | 设置全局用户名 |
| `git config --global user.email "邮箱"` | 设置全局邮箱  |
| `git config --list`                   | 查看所有配置项 |

***

#### **仓库操作**

| 命令                           | 说明                   |
| :--------------------------- | :------------------- |
| `git init`                   | 初始化新仓库               |
| `git clone <仓库地址>`           | 克隆远程仓库到本地            |
| `git remote add <别名> <仓库地址>` | 添加远程仓库别名（如 `origin`） |
| `git remote -v`              | 查看远程仓库地址             |

***

#### **提交与修改**

| 命令                          | 说明                          |
| :-------------------------- | :-------------------------- |
| `git status`                | 查看工作区状态                     |
| `git add <文件>`              | 将文件添加到暂存区（`git add .` 添加所有） |
| `git commit -m "消息"`        | 提交暂存区内容（`-a` 跳过 `git add`）  |
| `git diff`                  | 查看未暂存的改动                    |
| `git diff --staged`         | 查看已暂存的改动                    |
| `git restore <文件>`          | 丢弃工作区未暂存的修改（Git 2.23+）      |
| `git restore --staged <文件>` | 从暂存区移除文件（保留工作区修改）           |

***

#### **分支管理**

| 命令                       | 说明                   |
| :----------------------- | :------------------- |
| `git branch`             | 查看本地分支（`-a` 查看所有分支）  |
| `git branch <分支名>`       | 创建新分支                |
| `git checkout <分支名>`     | 切换分支                 |
| `git checkout -b <新分支名>` | 创建并切换到新分支            |
| `git merge <分支名>`        | 合并指定分支到当前分支          |
| `git branch -d <分支名>`    | 删除分支（`-D` 强制删除未合并分支） |

***

#### **远程协作**

| 命令                                    | 说明                                       |
| :------------------------------------ | :--------------------------------------- |
| `git push <远程名> <分支名>`                | 推送本地分支到远程（如 `git push origin main`）      |
| `git pull <远程名> <分支名>`                | 拉取远程分支并合并（等价于 `git fetch` + `git merge`） |
| `git fetch <远程名>`                     | 下载远程仓库最新内容（不自动合并）                        |
| `git push --set-upstream <远程名> <分支名>` | 推送并关联远程分支（首次推送时使用）                       |

***

#### **撤销与回退**

| 命令                        | 说明                               |
| :------------------------ | :------------------------------- |
| `git reset HEAD~1`        | 回退到上一次提交（保留工作区修改，`--soft` 保留暂存区） |
| `git reset --hard HEAD~1` | 彻底回退到上一次提交（丢弃所有修改）               |
| `git revert <提交哈希>`       | 撤销指定提交（生成新提交记录）                  |
| `git stash`               | 储藏当前未提交的修改（`pop` 恢复，`list` 查看列表） |

***

#### **日志与历史**

| 命令                | 说明                                       |
| :---------------- | :--------------------------------------- |
| `git log`         | 查看提交历史（`--oneline` 简洁模式，`--graph` 图形化分支） |
| `git log -p <文件>` | 查看文件的详细修改历史                              |
| `git blame <文件>`  | 逐行显示文件修改人（`-L 10,20` 查看指定行数）             |
| `git show <提交哈希>` | 查看某次提交的详细内容                              |

***

#### **标签管理**

| 命令                     | 说明                         |
| :--------------------- | :------------------------- |
| `git tag`              | 查看所有标签                     |
| `git tag <标签名>`        | 创建轻量标签（`-a` 创建含注释的标签）      |
| `git push <远程名> <标签名>` | 推送标签到远程仓库（`--tags` 推送所有标签） |
| `git tag -d <标签名>`     | 删除本地标签                     |

***

#### **实用技巧**

1.  **忽略文件**：创建 `.gitignore` 文件，定义需要忽略的文件/目录（如 `*.log`, `/build/`）。
2.  **别名简化命令**：

    1.  `` git config --global alias.co checkout # 用 `git co` 代替 `git checkout` git config --global alias.br branch # 用 `git br` 代替 `git branch` ``
3.  **查找提交**：

    1.  `git log --grep="关键词" # 按提交消息搜索 git log -S"函数名" # 按代码内容搜索`

***

**常用组合命令示例**：

    # 1. 提交并推送到远程分支
    git add .
    git commit -m "更新功能"
    git push origin main

    # 2. 合并分支并解决冲突
    git checkout main
    git merge feature-branch
    # 解决冲突后提交
    git add .
    git commit -m "合并feature分支"
    git push

    # 3. 临时切换任务（储藏修改）
    git stash
    git checkout hotfix-branch
    # 修复后回到原分支
    git checkout feature-branch
    git stash pop

***

**小贴士**：

*   使用 `git help <命令>` 查看详细帮助（如 `git help reset`）。
*   提交消息遵循清晰规范（如 [Conventional Commits](https://www.conventionalcommits.org/)）。

保存这张卡片，轻松驾驭 Git 版本控制！ 🛠️🐙
