# Ansible-Note

* Ansible is an open-source automation tool used for configuration management, application deployment, and task automation. It follows an agentless architecture, using SSH or WinRM to communicate with remote systems. 

* Ansible uses YAML-based playbooks to define automation tasks, making it simple and human-readable.

* It is widely used for automating infrastructure provisioning, orchestration, and compliance management.

* Ansible ensures systems are in the desired state without requiring manual intervention.

### Ansible helps us with several important tasks, primarily focusing on:

#### Software Installation:
1. Ansible automates the process of installing software on multiple servers. You can use Ansible to easily manage the installation of packages and applications across different systems.

2. Server Configuration Management:
Ansible helps manage server configurations. This means you can:

* Add new configurations
* Update existing configurations
* Delete configurations on your servers, all in a streamlined, automated way.

3. Application Deployment:
One of the most important uses of Ansible is for deploying web applications or any kind of application on a server. You can automate the entire process of deploying, updating, or managing applications on your infrastructure, which saves time and reduces the chances of errors.

### Ansible Playbook

Ansible Playbook is a YAML file that defines a set of instructions or tasks for automating the configuration and management of systems. It describes the steps Ansible should take to configure, deploy, and manage applications, services, or infrastructure across a set of hosts (servers, virtual machines, etc.).

Below is a example of a simple Ansible playbook.

```
---
- name: Configure web server
  hosts: webservers
  become: yes
  tasks:
    - name: Install Apache HTTP server
      apt:
        name: apache2
        state: present

    - name: Ensure Apache is started
      service:
        name: apache2
        state: started
        enabled: yes
```

* ```hosts:``` Specifies the group of machines the playbook will run on. In this case, it's a group of hosts labeled ```webservers``` (as defined in your Ansible inventory).
* ```become: yes:``` This indicates that the tasks should be run with elevated (root) privileges (using sudo).
* ```tasks:``` This section lists all tasks to be executed:
    1. Install Apache HTTP server using the apt package manager (for Debian-based systems).
    2. Start the Apache service and ensure it is enabled to start on boot using the service module.

To run a playbook, use the ```ansible-playbook``` command:

```ansible-playbook playbook.yml```

Benefits of a Ansible playbook can be describe as below:

* **Automation:** Playbooks allow you to automate repetitive tasks, like configuring servers, deploying applications, and managing infrastructure.
* **Reusability:** You can define tasks, roles, and configurations in playbooks and reuse them across different environments.
* **Declarative:** Playbooks describe what you want to achieve, not how to achieve it. Ansible automatically handles the execution order, dependencies, and error handling.
* **Idempotency:** Running a playbook multiple times will not cause unintended side effects. If a task has already been executed (e.g., a package is already installed), Ansible will skip that task.