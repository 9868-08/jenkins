# repository for work in sbernank  
  
To jenkins install ansible via playbooks:  
ansible-playbook -l virtualbox -i hosts ./playbook_java.yml  
ansible-playbook -l virtualbox -i hosts ./playbook_jenkins.yml  
  
To run application along in docker:  
docker build -t python-hello-world .  
docker run --name  hellow-world  python-hello-world  
