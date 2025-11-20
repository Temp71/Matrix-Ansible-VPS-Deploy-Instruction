# Matrix-Ansible-VPS-Deploy-Instruction
This is an Instruction on how to deploy [spantaleev/matrix-docker-ansible-deploy](https://github.com/spantaleev/matrix-docker-ansible-deploy) on a Server tested on Hetzner

After you have successfully configured this you can:
- 📲 login with QR code 
- 📞 use the Audio/Video call feauture inside Element 
- 🌎 Have an Element Web instance (element.mydomain.com) 
- 🔐 Matrix Authentication Service is properly working 
- 🤝 federation 
  
  Important READ [prerequisites.md](https://github.com/spantaleev/matrix-docker-ansible-deploy/blob/master/docs/prerequisites.md)

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
12. After you configured the vars.yml go back to the matrix-docker-ansible-deploy folder and do "cp examples/hosts inventory/hosts" and then "nano inventory/hosts" to configure the VPS where you want to install your matrix Server.
13. Make sure youre again in matrix-docker-ansible-deploy and then do "git pull", "rm -rf roles/galaxy; ansible-galaxy install -r requirements.yml -p roles/galaxy/ --force" and then "ansible-playbook -i inventory/hosts setup.yml --tags=install-all,ensure-matrix-users-created,start --ask-pass".
14. If it was successful without failed services you can create an Admin user on your Server with this command:
"ansible-playbook -i inventory/hosts setup.yml --extra-vars='username=YOURUSERNAME password=YOURPASSWORD admin=yes' --tags=register-user --ask-pass".
For regular users just do admin=yes' to admin=no'

Done :)


