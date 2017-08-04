# openstack-swift-docker

## usage

Build docker image

```bash
docker build -t openstack-swift-docker .
```

Prepare datavolume

```bash
docker run -v /srv --name SWIFT_DATA busybox
```

Run container

```bash
docker run -d --name openstack-swift -p 12345:8080 --volumes-from SWIFT_DATA -t openstack-swift-docker
```

Check container

```bash
docker logs openstack-swift
docker ps

```

Verify functionality

```bash
swift -A http://127.0.0.1:12345/auth/v1.0 -U test:tester -K testing stat
swift -A http://127.0.0.1:12345/auth/v1.0 -U test:tester -K testing list
```

