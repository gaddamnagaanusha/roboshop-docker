lsblk
sudo growpart /dev/nvme0n1 4
sudo lvextend -L+30G /dev/RootVG/varVol
sudo xfs_growfs /var

sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo

sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

sudo systemctl start --now docker
sudo systemctl enable --now docker
sudo systemctl status --now docker


sudo usermod -aG docker ec2-user

