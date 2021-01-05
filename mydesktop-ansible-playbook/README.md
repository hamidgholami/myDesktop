Ubuntu Preparation
=========

An ansible role for preparing `Ubuntu 20.04(focal)` as a suitable *desktop* with whole packages which are need.

Requirements
------------

* By default, when Ubuntu is first installed, remote acces via `ssh` is not allowed. Enabling SSH on Ubuntu is fairly strightforward.
```bash
sudo apt install openssh-server -y
```
* Then grant sudo privilages to Ubuntu user. 

Step 1
--------------
In ansible machine (Other client that should access via ssh to Ubuntu) clone project and cd on it.
```bash
git clone https://github.com/hamidgholami/myDesktop.git && cd "$(basename "$_" .git)"/mydesktop-ansible-playbook
```

Step 2
--------------

Fisrt of all, Edit `inventory.yml` and fill all variables.
```yml
all:
  children:
       myUbuntu:
          vars:
            ansible_user: UBUNTU_USER_NAME
            ansible_become: yes
            ansible_become_password: UBUNTU_PASSWORD
          hosts:
            ubuntu:
              ansible_host: X.X.X.X # or localhost
              git_config_username: "USER_NAME"
              git_config_email: "x.xxxx@mail.com"
```

Step 3
------------

Put all the required files into a directory with `debFiles` name in the path below.
```bash
# roles/ubuntuPreparation/files/
.
└── roles
    └── ubuntuPreparation
        ├── defaults
        ├── files
        │   ├── apt_keys # All apt-key files for Ubuntu's repositories
        │   ├── debFiles # All .deb files
        │   │   ├── google-chrome-stable_current_amd64.deb
        │   │   ├── HipChat4-4.30.5.1682-Linux.deb
        │   │   ├── jitsi_2.10.5550-1_amd64.deb
        │   │   ├── jitsi-archive-keyring_1.0.1_all.deb
        │   │   ├── libssl1.0.2_1.0.2u-1~deb9u1_amd64.deb
        │   │   ├── vagrant_2.2.9_x86_64.deb
        │   │   └── VNC-Viewer-6.20.529-Linux-x64.deb
        │   └── certs # All certificates (*.crt)
        ├── handlers
        ├── meta
        ├── tasks
        ├── tests
        └── vars
```

Step 4
----------------

Follow to run `ansible-playbook` as below.
```bash
ansible-playbook -i inventory.yml ubuntuPreparation.yml
```

**************

**Author**: Hamid Gholami (hidgholami@gmail.com)

[LinkedIn](https://www.linkedin.com/in/hamid-gholami)
&nbsp;
[GitHub](https://github.com/hamidgholami)
&nbsp;
[Twitter](https://www.twitter.com/045_hamid)

