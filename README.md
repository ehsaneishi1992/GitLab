export this variable
```bash
export GITLAB_HOME=/Users/apple/Documents/GitHub/GitLab
```
and up your gitlab docker compose
```bash
docker compose up -d
```
to show and use password run this command
```bash
docker exec -it gitlab cat /etc/gitlab/initial_root_password | grep 'Password:'
```
after up gitlab and jenkins to connect network these two containers must be create shared-network ann connect containers to this network
```bash
docker network create shared-network /
docker network connect shared-network gitlab /
docker network connect shared-network jenkins
```
Use the container name gitlab as the hostname in Jenkins
