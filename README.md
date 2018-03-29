# Ansible to Docker

> Example of connecting Ansible to a Docker container.

## Ping pong test

```
docker run -itd --name foobar centos:7
ansible -i foobar, -c docker -m ping all
foobar | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

## Playbook

```
docker run -itd --name foobar centos:7
ansible-playbook -i foobar, -c docker playbook.yml
docker exec foobar awk -F : '{ print $1 }' /etc/passwd | sort | grep foo
foo
```

## Links

* https://just-thor.com/2017/02/how-to-connect-to-docker-from-ansible/