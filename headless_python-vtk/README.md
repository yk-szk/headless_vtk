# Off-screen vtk rendering

## Run a container    
    docker run -it --privileged \
            --runtime=nvidia \
            -e BUSID=PCI:6:0:0 \
            -e SCREEN_RESOLUTION=1280x1024 \
            syuki/headless-python-vtk

## Run the folloing commands in the container
    nvidia-xconfig -a --virtual=$SCREEN_RESOLUTION --allow-empty-initial-configuration --busid $BUSID

<details><summary>output message</summary>
root@983127f81afe:/work# nvidia-xconfig -a --virtual=$SCREEN_RESOLUTION --allow-empty-initial-configuration --busid $BUSID

WARNING: Unable to locate/open X configuration file.

Package xorg-server was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found
Option "AllowEmptyInitialConfiguration" "True" added to Screen "Screen0".
New X configuration file written to '/etc/X11/xorg.conf'
</details>

    Xorg :0 &

<details><summary>output message</summary>
[1] 18
root@983127f81afe:/work#
X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-128-generic x86_64 Ubuntu
Current Operating System: Linux 983127f81afe 4.15.0-58-generic #64-Ubuntu SMP Tue Aug 6 11:12:41 UTC 2019 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-58-generic root=UUID=ab6b30e2-dc71-4e39-a182-dc1ff263b7df ro
Build Date: 10 August 2018  09:33:05AM
xorg-server 2:1.18.4-0ubuntu0.8 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.33.6
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 13 00:08:53 2019
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
</details>

    export DISPLAY=:0
    python3 render.py