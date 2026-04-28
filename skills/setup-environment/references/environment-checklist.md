# 环境检测与安装清单

## 语言运行时

### Node.js

| 项目 | 内容 |
|------|------|
| 检测命令 | `node --version` |
| 推荐安装方式 | 通过 nvm 安装：`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh \| bash && nvm install --lts` |
| 推荐理由 | 支持多版本管理，项目间互不干扰，切换方便 |
| 备选方式 | 1. fnm：`curl -fsSL https://fnm.vercel.app/install \| bash && fnm install --lts` — 更快，Rust 实现<br>2. 官网安装包：https://nodejs.org — 适用于不需要多版本的场景 |
| 验证命令 | `node --version && npm --version` |
| 潜在风险 | nvm 会修改 shell 配置文件（.bashrc / .zshrc），添加初始化脚本 |

### Python

| 项目 | 内容 |
|------|------|
| 检测命令 | `python3 --version` |
| 推荐安装方式 | 通过 pyenv 安装：`curl https://pyenv.run \| bash && pyenv install 3.12` |
| 推荐理由 | 支持多版本管理，隔离系统 Python，避免污染系统环境 |
| 备选方式 | 1. Homebrew（macOS）：`brew install python@3.12` — 简单快捷<br>2. 官网安装包：https://python.org — 适用于 Windows |
| 验证命令 | `python3 --version && pip3 --version` |
| 潜在风险 | 不要覆盖系统自带 Python（macOS / Linux），可能导致系统工具异常 |

### Java

| 项目 | 内容 |
|------|------|
| 检测命令 | `java --version` |
| 推荐安装方式 | 通过 SDKMAN 安装：`curl -s "https://get.sdkman.io" \| bash && sdk install java` |
| 推荐理由 | 支持管理多个 JDK 版本和发行版（Temurin、GraalVM 等） |
| 备选方式 | 1. Homebrew（macOS）：`brew install openjdk` — 快速安装单一版本<br>2. 手动下载 Adoptium：https://adoptium.net |
| 验证命令 | `java --version && javac --version` |
| 潜在风险 | 需正确设置 JAVA_HOME 环境变量 |

### Go

| 项目 | 内容 |
|------|------|
| 检测命令 | `go version` |
| 推荐安装方式 | 官方安装包：https://go.dev/dl/ 下载对应平台安装包 |
| 推荐理由 | Go 官方安装方式简单可靠，自带版本管理（`go install golang.org/dl/go1.x`） |
| 备选方式 | 1. Homebrew（macOS）：`brew install go`<br>2. goenv：`goenv install 1.22` — 需要频繁切换版本时 |
| 验证命令 | `go version` |
| 潜在风险 | 需确认 GOPATH 和 GOROOT 配置正确 |

### Rust

| 项目 | 内容 |
|------|------|
| 检测命令 | `rustc --version` |
| 推荐安装方式 | `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs \| sh` |
| 推荐理由 | rustup 是 Rust 官方唯一推荐的安装和版本管理工具 |
| 备选方式 | Homebrew（macOS）：`brew install rust` — 不推荐，缺少 rustup 的工具链管理能力 |
| 验证命令 | `rustc --version && cargo --version` |
| 潜在风险 | 会修改 PATH（写入 shell 配置文件） |

## 包管理器

### npm / yarn / pnpm

| 工具 | 检测命令 | 推荐安装方式 | 推荐理由 |
|------|----------|-------------|----------|
| npm | `npm --version` | 随 Node.js 自带 | — |
| yarn | `yarn --version` | `corepack enable && corepack prepare yarn@stable --activate` | Node.js 内置 corepack 管理，无需全局安装 |
| pnpm | `pnpm --version` | `corepack enable && corepack prepare pnpm@latest --activate` | 同上，且 pnpm 节省磁盘空间 |

### pip / Poetry / uv

| 工具 | 检测命令 | 推荐安装方式 | 推荐理由 |
|------|----------|-------------|----------|
| pip | `pip3 --version` | 随 Python 自带 | — |
| Poetry | `poetry --version` | `curl -sSL https://install.python-poetry.org \| python3 -` | 官方推荐方式，独立安装不污染项目环境 |
| uv | `uv --version` | `curl -LsSf https://astral.sh/uv/install.sh \| sh` | 极快的 Python 包管理器，Rust 实现 |

### Homebrew（macOS / Linux）

| 项目 | 内容 |
|------|------|
| 检测命令 | `brew --version` |
| 推荐安装方式 | `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` |
| 推荐理由 | macOS 生态事实标准，软件包丰富 |
| 验证命令 | `brew --version && brew doctor` |
| 潜在风险 | 安装需要 Xcode Command Line Tools；会在 /usr/local（Intel）或 /opt/homebrew（Apple Silicon）下创建目录 |

## 数据库

### MySQL

| 项目 | 内容 |
|------|------|
| 检测命令 | `mysql --version` |
| 推荐安装方式 | Docker：`docker run --name mysql -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 -d mysql:8` |
| 推荐理由 | 隔离性好，不影响系统，易于清理和重建 |
| 备选方式 | 1. Homebrew（macOS）：`brew install mysql`<br>2. APT（Ubuntu）：`sudo apt install mysql-server` |
| 验证命令 | `mysql --version` 或 `docker exec mysql mysql --version` |
| 潜在风险 | Docker 方式需先安装 Docker；直接安装会启动后台服务占用端口 |

### PostgreSQL

| 项目 | 内容 |
|------|------|
| 检测命令 | `psql --version` |
| 推荐安装方式 | Docker：`docker run --name postgres -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres:16` |
| 推荐理由 | 同 MySQL，隔离性好 |
| 备选方式 | 1. Homebrew（macOS）：`brew install postgresql@16`<br>2. APT（Ubuntu）：`sudo apt install postgresql` |
| 验证命令 | `psql --version` 或 `docker exec postgres psql --version` |
| 潜在风险 | 同 MySQL |

### Redis

| 项目 | 内容 |
|------|------|
| 检测命令 | `redis-cli --version` |
| 推荐安装方式 | Docker：`docker run --name redis -p 6379:6379 -d redis:7` |
| 推荐理由 | 轻量，Docker 方式启停方便 |
| 备选方式 | 1. Homebrew（macOS）：`brew install redis`<br>2. APT（Ubuntu）：`sudo apt install redis-server` |
| 验证命令 | `redis-cli ping`（应返回 PONG） |
| 潜在风险 | 默认无密码，生产环境须配置认证 |

### MongoDB

| 项目 | 内容 |
|------|------|
| 检测命令 | `mongosh --version` |
| 推荐安装方式 | Docker：`docker run --name mongo -p 27017:27017 -d mongo:7` |
| 推荐理由 | 官方安装步骤繁琐，Docker 最省事 |
| 备选方式 | 1. Homebrew（macOS）：`brew tap mongodb/brew && brew install mongodb-community`<br>2. 官方 APT 源（Ubuntu） |
| 验证命令 | `mongosh --eval "db.version()"` |
| 潜在风险 | 默认无认证，注意不要暴露到公网 |

## 容器与编排

### Docker

| 项目 | 内容 |
|------|------|
| 检测命令 | `docker --version && docker compose version` |
| 推荐安装方式 | Docker Desktop：https://www.docker.com/products/docker-desktop/ |
| 推荐理由 | 官方推荐，含 Docker Engine + Compose + GUI，开箱即用 |
| 备选方式 | 1. Colima（macOS）：`brew install colima && colima start` — 轻量替代，无 GUI<br>2. 直接安装 Engine（Linux）：`curl -fsSL https://get.docker.com \| sh` |
| 验证命令 | `docker run hello-world` |
| 潜在风险 | Docker Desktop 商业使用需许可证（大型企业）；会占用较多系统资源 |

## 版本控制

### Git

| 项目 | 内容 |
|------|------|
| 检测命令 | `git --version` |
| 推荐安装方式 | macOS：`xcode-select --install`（含 Git）<br>Linux：`sudo apt install git` / `sudo yum install git` |
| 推荐理由 | 系统包管理器安装最稳定 |
| 备选方式 | Homebrew（macOS）：`brew install git` — 获取更新版本 |
| 验证命令 | `git --version` |
| 潜在风险 | 无明显风险 |

## 系统信息检测

| 检测项 | macOS 命令 | Linux 命令 |
|--------|-----------|------------|
| 操作系统版本 | `sw_vers` | `cat /etc/os-release` |
| 系统架构 | `uname -m` | `uname -m` |
| Shell 类型 | `echo $SHELL` | `echo $SHELL` |
| 磁盘空间 | `df -h /` | `df -h /` |
| 内存 | `sysctl hw.memsize` | `free -h` |
| CPU | `sysctl -n machdep.cpu.brand_string` | `lscpu` |
