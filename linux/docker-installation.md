### PREPARATION:
Start installing the required packages:
```
yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
```
Setup stable repository:
```
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```
then install yum-utils:
```
	yum install yum-utils
```	
with the output:
```	
		yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
		adding repo from: https://download.docker.com/linux/centos/docker-ce.repo
		grabbing file https://download.docker.com/linux/centos/docker-ce.repo to /etc/yum.repos.d/docker-ce.repo
		repo saved to /etc/yum.repos.d/docker-ce.repo
```

		  
### INSTALLATION:
- Install using repository

	install the latest stable version:
	```
		yum install docker-ce
	```	
	or install an older version with: 
	> yum install docker-ce-<VERSION_STRING> but first check what versions are available from our repositories:
	```
			yum list docker-ce --showduplicates | sort -r
			docker-ce.x86_64            18.03.1.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            18.03.0.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            17.12.1.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            17.12.0.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            17.09.1.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            17.09.0.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            17.06.2.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            17.06.1.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            17.06.0.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            17.03.2.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            17.03.1.ce-1.el7.centos             docker-ce-stable
			docker-ce.x86_64            17.03.0.ce-1.el7.centos             docker-ce-stable
			Available Packages
	```	
	then 
	```	
			yum install docker-ce-18.03.0.ce-1.el7.centos
   ```
	or downgrade to a previous version from the one already installed:
	```
		yum downgrade docker-ce-<VERSION_STRING>
		
		ie, yum install --skip-broken docker-ce-18.03.0.ce-1.el7.centos
	```	
	Finally:
	```
		systemctl enable docker
		Created symlink from /etc/systemd/system/multi-user.target.wants/docker.service to /usr/lib/systemd/system/docker.service.
		[root@reaper v3.11]#
		[root@reaper v3.11]# systemctl start docker
	```	
	And check it!!!!:
	```
	    $ docker run hello-world
		Unable to find image 'hello-world:latest' locally
		latest: Pulling from library/hello-world
		9bb5a5d4561a: Pull complete
		Digest: sha256:f5233545e43561214ca4891fd1157e1c3c563316ed8e237750d59bde73361e77
		Status: Downloaded newer image for hello-world:latest

		Hello from Docker!
	```
	This message shows that your installation appears to be working correctly.
	To generate this message, Docker took the following steps:
		 1. The Docker client contacted the Docker daemon.
		 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
			(amd64)
		 3. The Docker daemon created a new container from that image which runs the
			executable that produces the output you are currently reading.
		 4. The Docker daemon streamed that output to the Docker client, which sent it
			to your terminal.

	To try something more ambitious, you can run an Ubuntu container with:
	```
		 $ docker run -it ubuntu bash
     ```
		

### ERRORS when try to install for the first time:
```
	Error: Package: docker-ce-18.03.0.ce-1.el7.centos.x86_64 (docker-ce-stable)
			   Requires: container-selinux >= 2.9
	Error: Package: docker-ce-18.03.0.ce-1.el7.centos.x86_64 (docker-ce-stable)
			   Requires: pigz
	 You could try using --skip-broken to work around the problem
	 You could try running: rpm -Va --nofiles --nodigest
```
```	 
	yum install -y http://mirror.centos.org/centos/7/extras/x86_64/Packages/container-selinux-2.42-1.gitad8f0f7.el7.noarch.rpm
	container-selinux-2.42-1.gitad8f0f7.el7.noarch.rpm  
```
Then, first error dissaperared but second persists (https://blog.dbi-services.com/docker-ce-on-oracle-enterprise-linux-7/):
```
	Error: Package: docker-ce-18.03.0.ce-1.el7.centos.x86_64 (docker-ce-stable)
			   Requires: pigz
	 You could try using --skip-broken to work around the problem
	 You could try running: rpm -Va --nofiles --nodigest
```

Therfore we executed:
```
		yum install --skip-broken docker-ce-18.03.0.ce-1.el7.centos
		
		with the output:
		
			Packages skipped because of dependency problems:
			docker-ce-18.03.0.ce-1.el7.centos.x86_64 from docker-ce-stable
			libseccomp-2.3.1-3.el7.x86_64 from ol7_latest
			libtool-ltdl-2.4.2-22.el7_3.x86_64 from ol7_latest
```
Now add the repo:
```
	vi /etc/yum.repos.d/public-yum-ol7.repo
	
	[ol7_developer_EPEL]
	name=Oracle Linux $releasever Developement Packages ($basearch)
	baseurl=http://yum.oracle.com/repo/OracleLinux/OL7/developer_EPEL/$basearch/
	gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
	gpgcheck=1
	enabled=1
```
and execute again the docker install command as now the dependencies will be solved.

Finally we get:
```
	Running transaction
	  Installing : pigz-2.3.4-1.el7.x86_64                                                                                                                                                                        1/4

	  Installing : libtool-ltdl-2.4.2-22.el7_3.x86_64                                                                                                                                                             2/4

	  Installing : libseccomp-2.3.1-3.el7.x86_64                                                                                                                                                                  3/4

	  Installing : docker-ce-18.03.0.ce-1.el7.centos.x86_64                                                                                                                                                       4/4

	  Verifying  : libseccomp-2.3.1-3.el7.x86_64                                                                                                                                                                  1/4

	  Verifying  : docker-ce-18.03.0.ce-1.el7.centos.x86_64                                                                                                                                                       2/4

	  Verifying  : libtool-ltdl-2.4.2-22.el7_3.x86_64                                                                                                                                                             3/4

	  Verifying  : pigz-2.3.4-1.el7.x86_64                                                                                                                                                                        4/4


	Installed:
	  docker-ce.x86_64 0:18.03.0.ce-1.el7.centos


	Dependency Installed:
	  libseccomp.x86_64 0:2.3.1-3.el7                                       libtool-ltdl.x86_64 0:2.4.2-22.el7_3                                       pigz.x86_64 0:2.3.4-1.el7


	Complete!
```

