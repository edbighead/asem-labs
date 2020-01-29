## Task
In this task we will simulate adding users, installing nginx and deploying a static website from one host to another hosts using [ansible](https://docs.ansible.com/).

Fork the following repository [asem-labs-ansible](https://github.com/edbighead/asem-labs-ansible)

### Setup
* Run the followng command `docker-compose up`
* This will bring up 3 containers: `master, node-1, node-2`
* Use the following command to get into running container:
    `docker exec -it container_name sh`
* Generate ssh-key on **master** container and add it to `~/.ssh/authorized_keys` file on **node-*** containers (use `ssh-keygen` command, generate key without a password for simplicity)
* Create `/etc/ansible/hosts` [hosts file](https://docs.ansible.com/ansible/2.4/intro_inventory.html#hosts-and-groups) on **master** and add **node-1** and **node-2** container names to it.
* From **master** container, run the following command to test connectivity `ansible all -m ping`

### Writing playbooks
You can test your changes with the following command: `ansible-playbook playbook.yml`

* Use [group module](https://docs.ansible.com/ansible/latest/modules/group_module.html) to create *admin* group
* Use [user module](https://docs.ansible.com/ansible/latest/modules/user_module.html#user-module) to create a user with your name. User must be member of above created group, have `/bin/bash` as a default shell and account should expire on 28th February.
* Use [apt module](https://docs.ansible.com/ansible/latest/modules/apt_module.html) to install `nginx`
* Use [service module](https://docs.ansible.com/ansible/latest/modules/service_module.html) to start and enable `nginx` on startup
* Use [file module](https://docs.ansible.com/ansible/latest/modules/file_module.html) to create `/src/www` directory
* Use [template module](https://docs.ansible.com/ansible/latest/modules/template_module.html) to create `/src/www/index.html` file from `templates/index.j2`. See [playbook variables](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html)
* Use [replace module](https://docs.ansible.com/ansible/latest/modules/replace_module.html) to replace `root /var/www/html` in `/etc/nginx/sites-enabled/default` file to above created directory.
* Use [command module](https://docs.ansible.com/ansible/latest/modules/command_module.html) to restart nginx

### Advanced
* Optimize your playbook. Use variables as much as possible.
* Add multiple users using [loops](https://docs.ansible.com/ansible/latest/user_guide/playbooks_loops.html)
* Read about [ansible roles](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html). Add roles for:
    * Creating users
    * Installing nginx
* Separate your servers to groups in hosts file, add group vars. (See [documentation](https://docs.ansible.com/ansible/2.4/intro_inventory.html#hosts-and-groups))