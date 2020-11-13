Steps to Installing(reinstalling) Virtual Box and Vagrant

## Removing old versions ( if this is a fresh install ignore this step )

Run the following commands. IF the following commands do not give you a "COMMAND NOT FOUND" error
than follow the purging steps.

`vboxmanage --version`

`vagrant --version`



## Purging Vagrant ( IF the top commands actually gave out versions ) 

`sudo apt-get remove vagrant`

`sudo apt-get purge vagrant`

`sudo apt-get autoremove --purge vagrant`

Verify afterwards that command is not found with 

`vagrant --version`

## Purging VirtualBox: Killing the tasks

First we have to stop virtual box from running.  Run the following command:

`sudo ps aux | grep -i "vbox"`

You may see an output like this:

```
root        6078  0.0  0.0      0     0 ?        I<   09:00   0:00 [iprt-VBoxWQueue]
root        6081  0.0  0.0      0     0 ?        S    09:00   0:00 [iprt-VBoxTscThr]
user+   45105  0.0  0.0   9032  2616 pts/1    S+   13:53   0:00 grep --color=auto -i vbox
```

This means virtualbox processes are running and we have to turn them off.

** READ THE COMMAND FIRST BEFORE RUNNING IT **

`sudo kill -9 _PID_ # PID being the number responsible for that process`

Example of this would be 

```
sudo kill -9 6078
sudo kill -9 6081
```
You can ignore the ` --color=auto -i vbox` if you have that only process running.

### Purging VirtualBox: Removing VirtualBox

to uninstall virtualbox we will run:

`sudo apt-get remove --purge virtualbox`

To delete all virtual machines we will run:

`sudo rm ~/"VirtualBox VMs" -Rf`
`sudo rm ~/.config/VirtualBox/ -Rf`

Run the command to verify the command DOES NOT WORK: 

`vboxmanage --version`

**IF the above command DOES NOT SAY command not found, that means you have multiple versions of Virtualbox installed**

Run the following command to fix this, otherwise you can skip this step. You may need to run it multiple times.

`sudo apt-get remove --purge virtualbox`

Run this command to verify that the virtualbox has been uninstalled:

`vboxmanage --version` 

Restart your computer.

## Installing VirtualBox and Vagrant

**NOTE: At a time of this is written, I found that, VIRTUALBOX VER 6.1.16 and VAGRANT 2.2.13 work. (yes even for lhl bootcamp vagrantfile) so install those versions unless you want to try something custom.**


### VirtualBox installation

Go to virtualbox website and click the deb download for the corresponding linux ver you have installed.

https://www.virtualbox.org/wiki/Linux_Downloads

Once the Deb downloads, double click the deb file and install in the software center.

Verify that the virtualbox has been installed with this command:

`vboxmanage --version` 

### Vagrant installation

Go to this site and pick the version of Vagrant you need to install. ** NOTE some vagrant versions
will not be compatable with some Virtualbox versions. Its best to either go both latest OR research 
to see which one is compatable with which.**

https://releases.hashicorp.com/vagrant/


Verify that this worked with:

`vagrant --version`

Once both of these versions are installed, you can start creating your VM folder and 
adding the Vagrantfile into it to test if both were a success.


