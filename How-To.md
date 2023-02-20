How to Install Ansible on Oracle Linux 7
****************************************
1: yum update
2: yum install python3 python3-pip
3: pip3.6 install --upgrade pip 
4: yum -y install git ansible
5: mkdir -p /usr/share/ansible/modules
6: echo "library=/usr/share/ansible/modules" >> vi /etc/ansible/ansible.cfg
7: pip install --upgrade jinja2

How to Install oci sdk and oci module on control node(OL7)
********************************************************
The OCI Ansiblemodules supports OCI SDK configuration to control the authentication information to be used for executing a Play
So if a user has a SDK configuration file(~/.oci/config),
•ansible modules would use the information configured in the file when an ansible playbook that refers to OCI ansible modules is executed
•to authenticate the connection,and perform the action on an OCI resource.

# cat oci_config
[DEFAULT]
user=ocid1.user.oc1..xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
fingerprint=xx.xx.xx.xx.xx.xx.xx.xx.xx.xx
tenancy=ocid1.tenancy.oc1..xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
region=<OCI Region here>
key_file=<path to your private keyfile> # TODO


#vi /etc/yum.repos.d/ol7.repo
[ol7_developer]
name=OracleLinux $releasever Development Packages($basearch)
baseurl=https://yum.oracle.com/repo/OracleLinux/OL7/developer/$basearch/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
gpgcheck=0
enabled=1
[ol7_developer_EPEL]
name=Oracle Linux $releasever Development Packages($basearch)
baseurl=https://yum.oracle.com/repo/OracleLinux/OL7/developer_EPEL/$basearch/
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-oracle
gpgcheck=0
enabled=1

#yum -y install python-oci-sdk python-oci-cli

#cd /usr/share/ansible/modules
#git clone https://github.com/oracle/oci-ansible-modules.git
#cd oci-ansible-modules
#sudo ./install.py

Latest Doc here: https://docs.cloud.oracle.com/en-us/iaas/Content/API/SDKDocs/ansiblegetstarted.htm