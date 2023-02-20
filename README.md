# oci
oracle cloud infrastructure 

Ansible playbook Example ::

1: To build oci compute using ansible(https://github.com/shurabh/oci/blob/main/How-To.md)
Pre-requisite :
       
       * Ansible Control Node with oci ansible module and sdk installed
       
       * oci_config file with 600 perm
       
       [DEFAULT]
       user=ocid1.user.oc1..xxxxxxxxxxxxxxxxxxxxxxxxx
       fingerprint=xx.xx.xx.xx.xx.xx.xx.xx.xx.xx.xx.xx.xx.xx
       tenancy=ocid1.tenancy.oc1..xxxxxxxxxxxxxxxxxxxxxxxxx
       region=<<oci_region>>
       key_file=<path to your private keyfile> 
      
      * oci_api_key.pem (It is private key can be downloaded from oci console)
2: Clone the Repo

3: update values as per your infra in roles\compute-build\vars\main.yml

4: Dry run :
           ansible-playbook compute-build.yaml --check

5: Run Playbook :
           ansible-playbook compute-build.yaml
