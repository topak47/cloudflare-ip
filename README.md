# cloudflare-ip
这个Shell脚本的主要功能是更新Cloudflare域名的DNS记录，以实现动态IP地址的更新。

通过优选ip网站接口抓取来自 https://api.hostmonit.com/get_optimization_ip 的优化IP地址信息。

利用解析JSON响应并提取IP地址和线路类型，然后根据预设的线路类型列表将信息写入名为 result.csv 的CSV文件。

# 使用说明

auth_email="xxxx@qq.com"   #CloudFlare账户邮箱

auth_key="bcdaxxxxxxxxe8b1e61704c1bc"   #CloudFlare域名下的key,位置在域名概述页面点击右下角获取api key。

zone_name="qq.eu.org"   #你的主域名

record_name="b"       #自动更新的二级域名前缀,例如cloudflare的cdn用b，gcore的cdn用gcore，后面是数字

record_count=5        #二级域名个数，例如配置5个，则域名分别是b1、b2、b3、b4、b5。

preset_lines=("CM")   #定义要抓取的线路类型，可以同时选择("CM" "CU" "CT")cm代表移动，cu代表联通，ct代表电信


# 使用说明

您需要在您的计算机上安装以下工具和软件：

Bash: 该脚本是一个Bash脚本，因此您需要确保您的系统支持Bash。大多数Linux和Unix操作系统都默认安装了Bash。

curl: curl 是一个命令行工具，用于发送HTTP请求。您可以使用以下命令来检查是否已安装curl：curl --version。如果没有安装，您可以根据您的操作系统使用合适的包管理器进行安装。

jq: jq 是一个轻量级的命令行JSON处理工具，用于解析和操作JSON数据。您可以使用以下命令来检查是否已安装jq：jq --version。如果没有安装，您可以根据您的操作系统使用合适的包管理器进行安装。

在大多数Linux系统中，您可以使用以下命令来安装缺少的工具：

### 对于Debian/Ubuntu系统：

运行下面命令：
sudo apt-get update
sudo apt-get install curl jq

### 对于Red Hat/CentOS系统：

运行下面命令：
sudo yum install curl jq

### 对于macOS系统，您可以使用Homebrew进行安装：

运行下面命令：
brew install curl jq


### 运行脚本使用以下命令：

./cloudflare-ip.sh

