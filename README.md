# ansible-plays-userManagement
Ansible playbook for managing or creating single or multiple users.

in order to distribute your public key to server:
1) use ssh-keygen to create public/private key

2) update ansible-plays-userManagement/sshPassLess/servers and add your servers ip in each line

3) run ansible-plays-userManagement/sshPassLess/copy-id.sh

-----------------------------------------------------------------------
to create usernames or update the user specifications:

1) update the inventory files. dont forget to send you public key to those servers.
	ansible-plays-userManagement/environments/inventory

2) then update your usernames and password in joson format.
	ansible-plays-userManagement/roles/user_management/tasks/variables/userpass.yml

3) to update the host part in playbook

4) in order to double check the effected servers run this command:
ansible-playbook -i .../inventory ansible-plays-userManagement/roles/user_management/tasks/updateUser.yaml --list-hosts

5) in order to verify the playbook syntax:
ansible-playbook -i .../inventory ansible-plays-userManagement/roles/user_management/tasks/updateUser.yaml --syntax-check -vv

6) in order to run the playbook and save the stdout for future reference:
ansible-playbook -i .../inventory ansible-plays-userManagement/roles/user_management/tasks/updateUser.yaml -vv 2>&1> result.out

------------------------------------------------------------------------
to remove users from hosts do as follow:

1) update the public key in the destinations and inventory file from ansible controller

2) update the usernames that you want to eliminate from desitnations:
	ansible-plays-userManagement/roles/user_management/tasks/variables/removeUser.yaml

3) update the host section in playbook
	ansible-plays-userManagement/roles/user_management/tasks/removeUser.yaml

4) in order to double check the effected servers run this command:
ansible-playbook -i .../inventory ansible-plays-userManagement/roles/user_management/tasks/removeUser.yaml --list-hosts

5) in order to verify the playbook syntax:
ansible-playbook -i .../inventory ansible-plays-userManagement/roles/user_management/tasks/removeUser.yaml --syntax-check -vv

6) in order to run the playbook and save the stdout for future reference:
ansible-playbook -i .../inventory ansible-plays-userManagement/roles/user_management/tasks/removeUser.yaml -vv 2>&1> result.out







