# jenkins
jenkins install ansible playbooks:

ansible-playbook -l server1 -i hosts ./playbook_java.yml
ansible-playbook -l server1 -i hosts ./playbook_jenkins.yml

docker build -t python-hello-world .
docker run --name  hellow-world  python-hello-world
