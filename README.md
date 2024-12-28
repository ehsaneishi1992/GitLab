up your gitlab docker compose
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

## Create a Backup Script

Backup Command: Create a script that runs the GitLab backup command. This command will create a backup of your GitLab instance.

```bash
#!/bin/bash
# Define backup directory
BACKUP_DIR="/path/to/your/backup/gitlab"

# Create a backup
docker exec -t gitlab gitlab-backup create STRATEGY=copy

# Move the backup to the desired directory
docker cp gitlab:/var/opt/gitlab/backups $BACKUP_DIR
```

Make the Script Executable: Save the script as gitlab_backup.sh and make it executable.
```bash
chmod +x gitlab_backup.sh
```
## Schedule the Backup with Cron

Edit Crontab: Open the crontab configuration to schedule the backup script to run daily.
```bash
crontab -e
```
Add Cron Job: Add the following line to schedule the backup at a specific time (e.g., every day at 2 AM).
```bash
0 2 * * * /path/to/gitlab_backup.sh
```
