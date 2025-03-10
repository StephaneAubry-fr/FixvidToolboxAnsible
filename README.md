# FixvidToolboxAnsible
    
    scp -r ~/W/FixvidToolboxAnsible toolbox-dev:~/

    sudo mv /home/provisioner/FixvidToolboxAnsible/ /home/deployer/
    sudo chown -R deployer: /home/deployer/FixvidToolboxAnsible
    sudo su deployer


   
    docker exec -i confluence cat confluence.cfg.xml


    cd ./FixvidToolboxAnsible
    ansible-playbook -i inventory.ini playbook-backup.yml
    ansible-playbook playbook-backup.yml

    ansible-inventory -i inventory.ini --list -y
    ansible all -i inventory-dev.ini -m ping
    ansible-playbook -i inventory.ini playbook-backup.yml

    ansible-playbook -i inventory.ini playbook-docker.yml --syntax-check
    ansible-playbook -i inventory.ini playbook-restore.yml


    docker stop confluence
    docker exec -i confluence-db psql -U confluence-dbuser -d confluence-db < /tmp/backup/devops/backup_confluence.sql
    docker start confluence

    docker exec -i atlassian-db psql --help
    docker exec -it atlassian-db psql -U atlassian-dbuser -d atlassian-db 
    docker exec -it atlassian-db psql -U confluence-dbuser -d atlassian-db
    docker exec -it atlassian-db psql -U jira-dbuser -d atlassian-db

    docker exec -i atlassian-db psql -U atlassian-dbuser -d atlassian-db -c 'select current_schema;'


    CREATE USER Toto WITH PASSWORD pwd;
    \du
    \l




    jdbc:postgresql://10.0.2.10:8060/atlassian-db?currentSchema=confluence

