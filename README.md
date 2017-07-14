[XOOPS 校園網路輕鬆架](http://campus-xoops.tn.edu.tw/)

# 1. 下載與安裝
  - 取得 docker image
```bash
$ docker pull lyshie/lamp-xoops
```
  - 取得 XOOPS 網頁檔案與 MySQL 資料庫檔案
```bash
$ wget https://raw.githubusercontent.com/lyshie/lamp-xoops/master/xoops.tgz
```

# 2. 解壓縮資料檔案
```bash
$ cd /opt
```
```bash
$ tar xvfz xoops.tgz
```

# 3. 啟動 LAMP
繼承自 [linode/lamp](https://hub.docker.com/r/linode/lamp/)，加入 [supervisord](http://supervisord.org/) 啟動 apache2 與 mysql
```bash
$ docker run -d -p 80:80 -v /opt/xoops:/var/www -v /opt/xoops/mysql:/var/lib/mysql lyshie/lamp-xoops:latest
```
掛載以下的本機目錄，確保資料可以儲存：
  - /opt/xoops 為 XOOPS 網頁檔案
  - /opt/xoops/mysq 為 MySQL 資料庫檔案

# 3. 瀏覽網頁
http://127.0.0.1/

# 4. 安全性
  - XOOPS 預設登入「帳號 admin」、「密碼 123456」
  - MySQL 預設密碼「Admin2015」

# 5. Dockerfile
https://github.com/lyshie/lamp-xoops

# 6. 在 dcs.tn.edu.tw 平台執行 Docker 
```bash
$ apt-get install docker.io
```
在 dcs.tn.edu.tw 平台上執行 Docker 可以將現有的 Ubuntu 單純化，作業系統升級時套件相依性也簡化，儘可能可以升級至 Ubuntu 16.04.2 LTS。各個服務只在自己的 container 裡面執行，這一層的虛擬化讓這些服務可以快速佈署與轉移。
)
