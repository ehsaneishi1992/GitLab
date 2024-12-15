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
