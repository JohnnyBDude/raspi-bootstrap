# Set up Ansible to control your Raspberry Pi

[http://docs.ansible.com/ansible/latest/intro_installation.html](http://docs.ansible.com/ansible/latest/intro_installation.html)

## Control machine requirements

- python 2.6 or 2.7


## Control machine installation

Install pip:

```
sudo apt install python-pip
```

Install ansible:

```
sudo pip install ansible
```


## Managed node Requirements

Python 2.4 or later


## Test the control machine

add local machine among ansible hosts

```
echo "127.0.0.1" > ~/ansible_hosts
export ANSIBLE_INVENTORY=~/ansible_hosts
```

now test with a ping command

```
ansible all -m ping --ask-pass
```

Which may or may not fail:) depending on your
shh setup.


# Add Raspberry Pi to your inventory

if you have it listed as raspberry in `/etc/hosts/`

```
echo "raspberry	ansible_user=pi" > ~/ansible_hosts
export ANSIBLE_INVENTORY=~/ansible_hosts
```

now you can test using

```
ansible all -m ping
```

or running a command on it

```
ansible all -a "/bin/echo hello"
```


