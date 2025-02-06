# Automation with Ansible

## Automation Goal
Simplify Server Configuration and Webpage Deployment with Ansible. 
Leverage Ansible to automate:

1. Server setup and configuration
2. Deployment of a simple webpage

Reduce manual effort and increase efficiency in infrastructure management and deployment.

## Server Setup
### Create Two Servers
1. **Master Node**: Primary server for management and control
2. **Slave Node (Host)**: Secondary server for data replication and failover

## Prerequisites
### Environment Requirements
Ensure the following prerequisites are met:

- Python is installed on all servers
- Tech stack:
    - **Ansible** (automation tool)
    - **AWS** (cloud infrastructure)
    - **Linux** (Ubuntu distribution)

## Steps to Automate Server Configuration
### Step 1: Install Ansible
Ensure Ansible is installed on your control node (master server) by running the following commands:

```sh
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install -y ansible
ansible --version
```

### Step 2: Configure Ansible Hosts File
Edit `/etc/ansible/hosts` and update it with the following configuration:

```ini
[server]
server1 ansible_host=3.85.237.244 ansible_user=ubuntu

[all:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_ssh_private_key_file=/home/ubuntu/keys/ansible-key.pem
```

### Step 3: Verify Ansible Configuration
Run the following commands to verify the Ansible configuration:

```sh
ansible-inventory --list -y
ansible server1 -m ping
```
![Screenshot (31)](https://github.com/user-attachments/assets/4296207e-9040-46e8-ae14-6cbadecb7b4e)


## Deploy a Webpage using Ansible
### Step 1: Create a Webpage
Create a new file named `index.html` with your desired webpage content.

### Step 2: Create an Ansible Playbook
Create a new file named `deploy_webpage.yml` and add the following playbook configuration:

```yaml
- name: Deploy Webpage to Nginx
  become: yes
  hosts: server
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: latest
    
    - name: Copy webpage to server destination
      copy:
        src: index.html
        dest: /var/www/html
```

### Step 3: Run the Ansible Playbook
Deploy the webpage by running the Ansible playbook:

```sh
ansible-playbook -v deploy_webpage.yml
```
![Screenshot (30)](https://github.com/user-attachments/assets/bce13eed-091b-4057-8126-dde582ea6b17)


### Step 4: Access the Webpage
Access the deployed webpage at:

```
http://localhost/
```
![Screenshot (29)](https://github.com/user-attachments/assets/c42ab700-fccb-48db-8485-c760d55ca53c)

## Automation Outcome
### Server Setup and Webpage Deployment with Ansible
You have achieved automated setup and deployment of:

- **Nginx** on your server
- A sample **web page**
- **Persistent Nginx service**

Ansible has successfully automated your infrastructure configuration!
