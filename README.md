Minecraft server in Raspberry Pi
=========

Ansible for install Minecraft Server in Ubuntu Server OS for Raspberry Pi 
------------

Requirements
------------
Ansible (Tested in 1.9)
SSH access to servers (Recommended RSA keypairs for SSH access)


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

- hosts: '{{host}}'
  roles:
    - { role: /Users/jvherrera/repositories/minecraft_ansible/yauh.java8, when: host != 'pi' }
    - /Users/jvherrera/repositories/minecraft_ansible/minecraft

Usage
----------------
```bash
$:~/minecraft ansible-playbook  -i inventory.yml -u pi --sudo minecraft.yml  --extra-vars "host=pi boot=yes" 

```

Install Minecraft Server in K8s
----------------

1. Create a new namespace minecraft
```bash
$:~/minecraft $ kubectl create namespace minecraft
namespace/minecraft created
```
2. Create the deployment
```bash
$:~/minecraft kubectl create -f deployment-minecraft.yaml --namespace=minecraft
replicationcontroller/minecraft created
```


3. Check the rc just created
```bash
$:~/minecraft  kubectl get rc --namespace=minecraft
NAME        DESIRED   CURRENT   READY   AGE
minecraft   1         1         1       3m53s18. jvherrera@juanvi-HP-ZBook-14u-G5:~ kubectl 
```
4. Check the pods of the minecraft replicaset
```bash
$:~/minecraft kubectl get po --namespace=minecraft
NAME              READY   STATUS    RESTARTS   AGE
minecraft-7hzb2   1/1     Running   0          4m35s
```

5. Create the minecraft service
```bash
$:~/minecraft  kubectl create -f service-minecraft.yaml --namespace=minecraft
service/minecraft created
```
License
-------

GPL

Author Information
------------------

@jvicenteherrera
juanvicenteherrera.eu
