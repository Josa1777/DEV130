# Install Jupyter Notebook On CentOS7

## Perparation
1. Login as root to CentOS7 server by using Putty

2. Set hostname to your name <br>
```bash
hostnamectl set-hostname <your-name>.polines.ac.id
```

3. To make easier, disable firewall
```bash
systemctl stop firewalld
systemctl disable firewalld
firewall-cmd --state
sed -i 's/^SELINUX=.*/SELINUX=disabled/' /etc/selinux/config
reboot
```

4. Relogin using Putty after CentOS7 server restarted

5. Install epel-repository
```bash
yum install -y  epel-release
```

6. Upgrade CentOS7 to get latest update and patch
```bash
yum -y update && yum -y upgrade
```

7. Install netstat and wget
```bash
yum install -y net-tools
yum install -y wget
```

8. Create new user
```bash
adduser <your-name>
passwd <your-name>
usermod -aG wheel <your-name>
```

9. Create analyst group
```bash
groupadd analyst
```

10. Add **your-name** to **analyst** group
```bash
usermod -a -G analyst yava
groups yava
```

## Install Miniconda
1. Download miniconda
```bash
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

2. Install miniconda <br>
```bash
./Miniconda3-latest-Linux-x86_64.sh
```
Set miniconda location to: /opt/miniconda3
```bash
Anaconda3 will now be installed into this location:
/root/anaconda3

- Press ENTER to confirm the location
- Press CTRL-C to abort the installation
- Or specify a different location below

[/root/anaconda3] > > >  /opt/miniconda3
```
Let install modify .bashrc
```bash
Do you wish the installer to prepend the Anaconda3 install location
to PATH in your /root/.bashrc ? [yes|no]
[no] > > >  yes
```

3. Change group ownership of /opt/miniconda3 dorectory
```bash
chgrp -R analyst miniconda3
chmod -R ug+rwx /opt/miniconda3
```

4. Relogin using **your-name**
```bash
su - <your-name>
```

5. Initialize miniconda
```bash
/opt/miniconda3/conda init
conda config --set auto_activate_base false
```

6. Create environment in miniconda and install jupyter notebook
```bash
conda create -n training python=3
conda install jupyter
```

7. Start jupyter notebook
```bash
jupyter notebook --no-browser --ip="0.0.0.0" --port=8890
```

8. Open Jupyter notebook by using web broser <br>
Copy link given when jupter notebook started <br>
Paste the url <br>

9. Lets do the code and have fun 

