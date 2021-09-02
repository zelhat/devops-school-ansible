первоначальная подготовка на control node

sudo -i

yum install -y epel-release

yum install -y ansible git

useradd ansible

echo super__password | sudo passwd --stdin ansible

echo "ansible ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/ansible

su - ansible

ssh-keygen -q -t ecdsa -N "" -f /home/ansible/.ssh/id_ecdsa

git clone https://github.com/zelhat/devops-school-ansible.git

cd devops-school-ansible

ansible-playbook init.yml --ask-pass -e user_pass=super__password -u user__name
