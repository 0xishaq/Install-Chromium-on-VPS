Buat kalian yang garap node tapi ingin run garapan ektension di node supaya gak usah beli RDP nih atmint kasih tutorial install chromium buat run extension di VPS

1. install docker jika sudah ada skip

sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Docker version check
docker --version

2. cek timezone kalau pake contabo pasti Europe/Berlin

realpath --relative-to /usr/share/zoneinfo /etc/localtime

3.  install chromium

mkdir chromium
cd chromium
nano docker-compose.yaml

4. edit file docker-compose.yaml

---
services:
  chromium:
    image: lscr.io/linuxserver/chromium:latest
    container_name: chromium
    security_opt:
      - seccomp:unconfined #optional
    environment:
      - CUSTOM_USER=     #set username
      - PASSWORD=    #set password
      - PUID=1000
      - PGID=1000
      - TZ= #edit dengan timezone
      - CHROME_CLI=https://x.com/littlethingscap #optional
    volumes:
      - /root/chromium/config:/config
    ports:
      - 3010:3000   #Ganti 3010 jika ada IP conflict
      - 3011:3001   #Ganti 3011 jika ada IP conflict
    shm_size: "1gb"
    restart: unless-stopped

jika sudah tekan ctrl+x+y+enter

5. run docker chromium

cd $HOME && cd chromium

docker compose up -d

6. access chromium di server dengan http://Server_IP:3010/ atau 
https://Server_IP:3011/ sesuai port yang kita setting ganti server IP dengan IP VPS kalian contoh : https://127.0.0.1:3010

7. stop / delete chromium

docker stop chromium
docker rm chromium
docker system prune
