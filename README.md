# change-docker-location

**If you have any database running take a backup before applying the below** 

1. Stop docker
   `sudo systemctl stop docker`

2. Create new directory for docker data (I just used my $HOME)
	`mkdir ~/docker-data`

3. Create daemon.json under `/etc/docker`
```
{
  "data-root": "~/docker-data"
}
```


4. Copy everything from /var/lib/docker under your new directory
	`sudo rsync -aP /var/lib/docker/ ~/docker-data`

5. Rename the old directory
   `sudo mv /var/lib/docker /var/lib/docker.old`

6. Restart docker
   `sudo systemctl start docker`

7. If everything is ok you should see no differences in using docker containers

8. Delete the old data directory
   `sudo rm -rf /var/lib/docker.old`
