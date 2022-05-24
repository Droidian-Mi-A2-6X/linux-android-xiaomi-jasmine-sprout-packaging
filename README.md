You should follow [kernel compilation guide from droidian](https://github.com/droidian/porting-guide/blob/master/kernel-compilation.md) with few steps

First, clone this repository and assign it's path to PACKAGING_DIR

```
git clone https://github.com/Droidian-Mi-A2-6X/linux-android-xiaomi-jasmine-sprout-packaging
export PACKAGING_DIR="/path/to/linux-android-xiaomi-jasmine-sprout-packaging/"
```

Then, run docker command with "-v $PACKAGING_DIR:/buildd/sources/debian"

Example:
```
(host)$ docker run -v $PACKAGES_DIR:/buildd -v $KERNEL_DIR:/buildd/sources -v PACKAGING_DIR:/buildd/sources/debian -it quay.io/droidian/build-essential:bullseye-amd64 bash
```

If you are using a SELinux based system such as Fedora you do not need to install docker. Fedora comes with Podman built-in. You simply need to replace the text `docker` with `podman`. Also notice the `:Z` flag, this is required on SELinux based systems to relabel the files in the container to avoid permission denied errors.

Example:
```
(host)$ podman run -v $PACKAGES_DIR:/buildd:Z -v $KERNEL_DIR:/buildd/sources:Z -v PACKAGING_DIR:/buildd/sources/debian:Z -it quay.io/droidian/build-essential:bullseye-amd64 bash
```

Continue from [compiling](https://github.com/droidian/porting-guide/blob/master/kernel-compilation.md#compiling) section
