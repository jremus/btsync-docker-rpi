# Dockerfile to run BitTorrent Sync on Raspberry Pi

## How-To Build

1. Copy the BitTorrent Sync 1.4.111 tar archive `btsync_arm-1.4.111.tar.gz` into your local clone of this Git repository.

2. Build the Dockerfile as follows:

   ```
   docker build -t btsync .
   ```

## How-To Run

```
docker run -d \
	--restart=unless-stopped \
	-p 8888:8888 \
	-p 55555:55555 \
	--hostname="$HOSTNAME-docker-btsync" \
	-v "/etc/localtime":"/etc/localtime":ro \
	-v btsync-data:/var/opt/btsync \
	-v /mnt/hd1:/mnt/hd1 \
	--name="btsync" \
	btsync:latest
```
