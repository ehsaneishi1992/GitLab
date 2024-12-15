export this variable
```bash
export GITLAB_HOME=/Users/apple/Documents/GitHub/GitLab
```
and up your gitlab docker compose
```bash
docker compose up -d
```
```bash
docker exec -it gitlab cat /etc/gitlab/initial_root_password | grep 'Password:'
```
