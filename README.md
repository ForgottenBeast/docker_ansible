==What does it do?==
This role handles docker image building: since some of our images are made to
run either on an ARM or amd64 machine some tasks are run remotely on a raspberry
pi rancherOS instance. The multiarch manifest building is always done on an
x86_64 machine to save time.

Be advised that this role *DOES NOT CREATE CONTAINERS, ONLY IMAGES*

==Tags==

* *docker_install* installs docker
* *manifest_install* installs manifest-tool
* *docker_all_install* equivalent to both tags above
* *images* Build images based on the host cpu architecture
* *multiarch* Use manifests to build multiarch images. Only works if there are
armv7 *and* x86_64 images available and only runs on x86_64 hosts to avoid
golang version issues with manifest-tool.
* *clean*: destroy *all local images* to pull new ones from dockerhub, useful if
everything as already been updated and you just want to create new multiarch
images.
* *pull*: only pull images

==Run with vpn==
If you choose to make your images use a VPN you can add a vpn: True key to their
description in vars, that way a vpn client will also be added on the image and a
connect script will make sure all their traffic goes through it.
