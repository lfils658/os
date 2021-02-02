<div align="center">
  <br>
  <h1 align="center"><center>ZEZE OS</center></h1>
  <h3 align="center"><center>A clean, beautiful OS with universal compatiblity</center></h3>
  <br>
  <br>
</div>

<p align="center">
  This OS is based mainly on elementary OS. Below is the README for elemenatry OS:
</p>

---

## Building Locally

As elementary OS is built with the Debian version of `live-build`, not the Ubuntu patched version, it's easiest to build an elementary .iso in a Debian VM or container. This prevents messing up your host system too.

The following example uses Docker and assumes you have Docker correctly installed and set up:

 1) Clone this project & `cd` into it:

    ```
    git clone https://github.com/elementary/os && cd os
    ```

 2) Configure the channel in the `etc/terraform.conf` (stable, daily).

 3) Run the build:

    ```
    docker run --privileged -i -v /proc:/proc \
        -v ${PWD}:/working_dir \
        -w /working_dir \
        debian:latest \
        /bin/bash -s etc/terraform.conf < build.sh
    ```

 4) When done, your image will be in the `builds` folder.

## Raspberry Pi 4

```
docker run --privileged -i -v /proc:/proc \
    -v ${PWD}:/working_dir \
    -w /working_dir \
    debian:unstable \
    ./build-rpi.sh
```


## Further Information

More information about the concepts behind `live-build` and the technical decisions made to arrive at this set of tools to build an .iso can be found [on the wiki](https://github.com/elementary/os/wiki/Building-iso-Images).
