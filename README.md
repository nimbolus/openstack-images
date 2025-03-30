# openstack-images

Images for OpenStack cloud build with [diskimage-builder](https://docs.openstack.org/diskimage-builder/latest/index.html).

## Build

### Development

**Requirements:**
- Podman (running as root)

Prepare diskimage-builder image:
```sh
podman build -t diskimage-builder diskimage-builder
```

Build image:
```sh
podman run --rm -it --privileged \
    -v $PWD:/home/builder/openstack-images \
    -w /home/builder/openstack-images diskimage-builder \
    diskimage-builder images/debian.yml
```

### GitHub Workflow

![build-image](https://github.com/nimbolus/openstack-images/actions/workflows/build.yml/badge.svg)

Go to [Actions](https://github.com/nimbolus/openstack-images/actions/workflows/build.yml) and click on `Run workflow`.

Images can be downloaded from job artifacts.
