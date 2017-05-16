Cloud Modules
`````````````

.. toctree:: :maxdepth: 1


Amazon
------

.. toctree:: :maxdepth: 1

  cloudformation - create a AWS CloudFormation stack <cloudformation_module>
  ec2 - create, terminate, start or stop an instance in ec2, return instanceid <ec2_module>
  ec2_ami - create or destroy an image in ec2, return imageid <ec2_ami_module>
  ec2_ami_search - Retrieve AWS AMI for a given operating system. <ec2_ami_search_module>
  ec2_asg - Create or delete AWS Autoscaling Groups <ec2_asg_module>
  ec2_eip - associate an EC2 elastic IP with an instance. <ec2_eip_module>
  ec2_elb - De-registers or registers instances from EC2 ELBs <ec2_elb_module>
  ec2_elb_lb - Creates or destroys Amazon ELB. <ec2_elb_lb_module>
  ec2_facts - Gathers facts about remote hosts within ec2 (aws) <ec2_facts_module>
  ec2_group - maintain an ec2 VPC security group. <ec2_group_module>
  ec2_key - maintain an ec2 key pair. <ec2_key_module>
  ec2_lc - Create or delete AWS Autoscaling Launch Configurations <ec2_lc_module>
  ec2_metric_alarm - Create/update or delete AWS Cloudwatch 'metric alarms' <ec2_metric_alarm_module>
  ec2_scaling_policy - Create or delete AWS scaling policies for Autoscaling groups <ec2_scaling_policy_module>
  ec2_snapshot - creates a snapshot from an existing volume <ec2_snapshot_module>
  ec2_tag - create and remove tag(s) to ec2 resources. <ec2_tag_module>
  ec2_vol - create and attach a volume, return volume id and device map <ec2_vol_module>
  ec2_vpc - configure AWS virtual private clouds <ec2_vpc_module>
  elasticache - Manage cache clusters in Amazon Elasticache. <elasticache_module>
  rds - create, delete, or modify an Amazon rds instance <rds_module>
  rds_param_group - manage RDS parameter groups <rds_param_group_module>
  rds_subnet_group - manage RDS database subnet groups <rds_subnet_group_module>
  route53 - add or delete entries in Amazons Route53 DNS service <route53_module>
  s3 - S3 module putting a file into S3. <s3_module>

Azure
-----

.. toctree:: :maxdepth: 1

  azure - create or terminate a virtual machine in azure <azure_module>

Digital Ocean
-------------

.. toctree:: :maxdepth: 1

  digital_ocean - Create/delete a droplet/SSH_key in DigitalOcean <digital_ocean_module>
  digital_ocean_domain - Create/delete a DNS record in DigitalOcean <digital_ocean_domain_module>
  digital_ocean_sshkey - Create/delete an SSH key in DigitalOcean <digital_ocean_sshkey_module>

Docker
------

.. toctree:: :maxdepth: 1

  _docker_image (E) - manage docker images <_docker_image_module>
  docker - manage docker containers <docker_module>

Google
------

.. toctree:: :maxdepth: 1

  gc_storage - This module manages objects/buckets in Google Cloud Storage. <gc_storage_module>
  gce - create or terminate GCE instances <gce_module>
  gce_lb - create/destroy GCE load-balancer resources <gce_lb_module>
  gce_net - create/destroy GCE networks and firewall rules <gce_net_module>
  gce_pd - utilize GCE persistent disk resources <gce_pd_module>

Linode
------

.. toctree:: :maxdepth: 1

  linode - create / delete / stop / restart an instance in Linode Public Cloud <linode_module>

Misc
----

.. toctree:: :maxdepth: 1

  ovirt (E) - oVirt/RHEV platform management <ovirt_module>
  virt (E) - Manages virtual machines supported by libvirt <virt_module>

Openstack
---------

.. toctree:: :maxdepth: 1

  glance_image - Add/Delete images from glance <glance_image_module>
  keystone_user - Manage OpenStack Identity (keystone) users, tenants and roles <keystone_user_module>
  nova_compute - Create/Delete VMs from OpenStack <nova_compute_module>
  nova_keypair - Add/Delete key pair from nova <nova_keypair_module>
  quantum_floating_ip - Add/Remove floating IP from an instance <quantum_floating_ip_module>
  quantum_floating_ip_associate - Associate or disassociate a particular floating IP with an instance <quantum_floating_ip_associate_module>
  quantum_network - Creates/Removes networks from OpenStack <quantum_network_module>
  quantum_router - Create or Remove router from openstack <quantum_router_module>
  quantum_router_gateway - set/unset a gateway interface for the router with the specified external network <quantum_router_gateway_module>
  quantum_router_interface - Attach/Dettach a subnet's interface to a router <quantum_router_interface_module>
  quantum_subnet - Add/remove subnet from a network <quantum_subnet_module>

Rackspace
---------

.. toctree:: :maxdepth: 1

  rax - create / delete an instance in Rackspace Public Cloud <rax_module>
  rax_cbs - Manipulate Rackspace Cloud Block Storage Volumes <rax_cbs_module>
  rax_cbs_attachments - Manipulate Rackspace Cloud Block Storage Volume Attachments <rax_cbs_attachments_module>
  rax_cdb - create/delete or resize a Rackspace Cloud Databases instance <rax_cdb_module>
  rax_cdb_database - create / delete a database in the Cloud Databases <rax_cdb_database_module>
  rax_cdb_user - create / delete a Rackspace Cloud Database <rax_cdb_user_module>
  rax_clb - create / delete a load balancer in Rackspace Public Cloud <rax_clb_module>
  rax_clb_nodes - add, modify and remove nodes from a Rackspace Cloud Load Balancer <rax_clb_nodes_module>
  rax_dns - Manage domains on Rackspace Cloud DNS <rax_dns_module>
  rax_dns_record - Manage DNS records on Rackspace Cloud DNS <rax_dns_record_module>
  rax_facts - Gather facts for Rackspace Cloud Servers <rax_facts_module>
  rax_files - Manipulate Rackspace Cloud Files Containers <rax_files_module>
  rax_files_objects - Upload, download, and delete objects in Rackspace Cloud Files <rax_files_objects_module>
  rax_identity - Load Rackspace Cloud Identity <rax_identity_module>
  rax_keypair - Create a keypair for use with Rackspace Cloud Servers <rax_keypair_module>
  rax_meta - Manipulate metadata for Rackspace Cloud Servers <rax_meta_module>
  rax_network - create / delete an isolated network in Rackspace Public Cloud <rax_network_module>
  rax_queue - create / delete a queue in Rackspace Public Cloud <rax_queue_module>
  rax_scaling_group - Manipulate Rackspace Cloud Autoscale Groups <rax_scaling_group_module>
  rax_scaling_policy - Manipulate Rackspace Cloud Autoscale Scaling Policy <rax_scaling_policy_module>

Vmware
------

.. toctree:: :maxdepth: 1

  vsphere_guest - Create/delete/manage a guest VM through VMware vSphere. <vsphere_guest_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not neccessarily) less activity maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
