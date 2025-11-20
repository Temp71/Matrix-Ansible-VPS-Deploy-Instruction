# Matrix-Ansible-VPS-Deploy-Instruction
This is an Instruction on how to deploy spantaleev/matrix-docker-ansible-deploy on a Server tested on Hetzner

1. Get a VPS from Hetzner for example.
2. change VPS Password
3. Update VPS: "apt update && apt upgrade -y"
5. Allow all these Ports for using Video/Audio Calls, federation and the basic Matrix Server stuff (https://github.com/spantaleev/matrix-docker-ansible-deploy/blob/master/docs/prerequisites.md and https://github.com/spantaleev/matrix-docker-ansible-deploy/blob/master/docs/configuring-playbook-livekit-server.md#adjusting-firewall-rules). "sudo ufw allow ssh && sudo ufw allow 80/tcp && sudo ufw allow 443/tcp && sudo ufw allow 443/udp && sudo ufw allow 3478/tcp && sudo ufw allow 3478/udp && sudo ufw allow 5349/tcp && sudo ufw allow 5349/udp && sudo ufw allow 8448/tcp && sudo ufw allow 8448/udp && sudo ufw allow 7881/tcp && sudo ufw allow 7882/udp && sudo ufw allow 3479/udp && sudo ufw allow 5350/tcp && sudo ufw allow 49152:49172/udp && sudo ufw enable"
6. run this command to check which Ports have been allowed: "sudo ufw status".
7. Now youre done on the VPS.
8. Now from you your PC create a folder somewhere and clone this Repository "https://github.com/spantaleev/matrix-docker-ansible-deploy.git"
9. Go into matrix-docker-ansible-deploy folder and run these commands "mkdir -p inventory/host_vars/matrix.example.com" (example.com = your Domain so change it!)
10. download the vars.yml from here and put it in this folder inventory/host_vars/matrix.example.com/HERE.
11. checkout the configuration of the vars.yaml [Configuring-the-playbook.md](https://github.com/Temp71/Matrix-Ansible-VPS-Deploy-Instruction/blob/main/Configuring-the-playbook.md)

