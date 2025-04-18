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

    docker stop confluence
    docker rm -v confluence

    docker exec -i atlassian-db psql --help
    docker exec -it atlassian-db psql -U atlassian-dbuser -d atlassian-db 
    docker exec -it atlassian-db psql -U confluence-dbuser -d atlassian-db
    docker exec -it atlassian-db psql -U jira-dbuser -d atlassian-db

    docker exec -i confluence-db psql --help
    docker exec -it confluence-db psql -U confluence_dbuser -d confluence-db 
    docker exec -it jira-db psql -U jira_dbuser -d jira-db
    docker exec -it artifactory-db psql -U artifactory_dbuser -d artifactory-db
    
    docker container stats

    docker exec -i atlassian-db psql -U atlassian-dbuser -d atlassian-db -c 'select current_schema;'

    jdbc:postgresql://10.0.2.10:8060/atlassian-db?currentSchema=confluence

## ssh-keyscan github.com

    ssh-keyscan -t ed25519 github.com > /var/jenkins_home/.ssh/known_hosts

## JFRog cli

# Create the keyrings directory if it doesn't exist
sudo mkdir -p /usr/share/keyrings;

# Download and save the JFrog GPG key to a keyring file
wget -qO - https://releases.jfrog.io/artifactory/api/v2/repositories/jfrog-debs/keyPairs/primary/public | sudo gpg --dearmor -o /usr/share/keyrings/jfrog.gpg

# Add the JFrog repository to your APT sources with the signed-by option
echo "deb [signed-by=/usr/share/keyrings/jfrog.gpg] https://releases.jfrog.io/artifactory/jfrog-debs focal contrib" | sudo tee /etc/apt/sources.list.d/jfrog.list


# Update the package list
sudo apt update;

# Install the JFrog CLI
sudo apt install -y jfrog-cli-v2-jf;

# Run the JFrog CLI intro command
jf intro;