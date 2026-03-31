* lsblk
* sudo growpart /dev/nvme0n1 4
* sudo lvextend -L+30G /dev/RootVG/varVol
* sudo xfs_growfs /var

* sudo dnf -y install dnf-plugins-core
* sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo

* sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

* sudo systemctl start --now docker
* sudo systemctl enable --now docker
* sudo systemctl status --now docker


* sudo usermod -aG docker ec2-user



* docker build -t mongodb:1.0.0 .
* docker images
* docker run -d --name mongodb mongodb:1.0.0
* docker ps -a
* cd ../catalogue/
* docker build -t catalogue:1.0.0 .
* docker run -d --name catalogue catalogue:1.0.0
* docker exec -it catalogue bash
* docker logs catalogue
* docker network create roboshop
* docker network ls
* docker network disconnect bridge mongodb
* docker network disconnect bridge catalogue
* docker network connect roboshop mongodb
* docker network connect roboshop catalogue
* docker exec -it catalogue bash
* curl http://localhost:8080/health
* cd ../frontend/
* docker build -t frontend:1.0.0 .
* docker run -d --name frontend -p 80:80 --network roboshop frontend:1.0.0
* docker ps
* now we can access the website with public ip of ec2 instance

* docker run -d --name redis --network roboshop redis:7
* docker build -t user:1.0.0 .
* docker run -d --name user --network roboshop user:1.0.0
* docker run -d --name cart --network roboshop cart:1.0.0
* 


