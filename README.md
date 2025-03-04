# FixvidToolboxAnsible
    
    scp -r ~/W/FixvidToolboxAnsible toolbox-dev:~/

    sudo mv /home/provisioner/FixvidToolboxAnsible/ /home/deployer/
    sudo chown -R deployer: /home/deployer/FixvidToolboxAnsible
    sudo su deployer
   

    cd ./FixvidToolboxAnsible
    ansible-playbook -i inventory.ini playbook-backup.yml

