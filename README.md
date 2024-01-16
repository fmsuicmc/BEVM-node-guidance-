سلام هستیم در خدمتتون با فول نود مشوق BEVM

اول از همه عضو دیسکورد بشید و برای یک ادرست EVM فاست بگیرید
https://discord.gg/fwsym3Je

از دو طریق باینری و داکر میشه نود رو نصب کرد که من داکرو رو آموزش میدم

سیستم مورد نیاز:

OS : Ubuntu 20.4+ 
CPU : 2 Cores 
RAM : 2 GB 
SSD : 300 GB

خب بریم برای نصب داکر : 
sudo apt-get remove docker docker-engine docker.io containerd runc

sudo apt-get update

sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release


sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg


echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin

sudo apt-get update
sudo apt-get upgrade
نصب پروژه و اجرا:
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

mkdir /var/lib/node_bevm_test_storage

sudo docker pull btclayer2/bevm:v0.1.1

حالا تو کد زیر ادرس والت EVM که بالا براش فاست گرفتید رو جایگزین کنین جای :replace_your_evm_address

sudo docker run -d -v /var/lib/node_bevm_test_storage:/root/.local/share/bevm btclayer2/bevm:v0.1.1 bevm "--chain=testnet" "--name=replace_your_evm_address" "--pruning=archive" --telemetry-url "wss://telemetry.bevm.io/submit 0"

خروجی شبیه زیر:

4bd1990d73dc9c91f260ef26a7f4c30c90fbb4679ea63395f9b2c7c55631a5e2

حالا با کد زیر لاگ بگیرید که همه چیز به خوبی داره کار میکنه

sudo docker logs -f 4bd1990d73dc9c91f260ef26a7f4c30c90fbb4679ea63395f9b2c7c55631a5e2

در پایان هم اگر نودتون به درستی کار کنه تو لینک زیر لیست میشه
https://telemetry.bevm.io/

امیدوارم استفاده کرده باشید 🫶🫶🫶
