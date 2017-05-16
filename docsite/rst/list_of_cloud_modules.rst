Cloud Modules
`````````````

.. toctree:: :maxdepth: 1

  xenserver_facts (E) - get facts reported on xenserver <xenserver_facts_module>

Amazon
------

.. toctree:: :maxdepth: 1

  cloudformation - Create or delete an AWS CloudFormation stack <cloudformation_module>
  cloudformation_facts (E) - Obtain facts about an AWS CloudFormation stack <cloudformation_facts_module>
  cloudtrail (E) - manage CloudTrail creation and deletion <cloudtrail_module>
  cloudwatchevent_rule (E) - Manage CloudWatch Event rules and targets <cloudwatchevent_rule_module>
  dynamodb_table (E) - Create, update or delete AWS Dynamo DB tables. <dynamodb_table_module>
  ec2 - create, terminate, start or stop an instance in ec2 <ec2_module>
  ec2_ami - create or destroy an image in ec2 <ec2_ami_module>
  ec2_ami_copy (E) - copies AMI between AWS regions, return new image id <ec2_ami_copy_module>
  ec2_ami_find - Searches for AMIs to obtain the AMI ID and other information <ec2_ami_find_module>
  ec2_ami_search (D) - Retrieve AWS AMI information for a given operating system. <ec2_ami_search_module>
  ec2_asg - Create or delete AWS Autoscaling Groups <ec2_asg_module>
  ec2_asg_facts (E) - Gather facts about ec2 Auto Scaling Groups (ASGs) in AWS <ec2_asg_facts_module>
  ec2_customer_gateway (E) - Manage an AWS customer gateway <ec2_customer_gateway_module>
  ec2_eip - manages EC2 elastic IP (EIP) addresses. <ec2_eip_module>
  ec2_elb - De-registers or registers instances from EC2 ELBs <ec2_elb_module>
  ec2_elb_facts (E) - Gather facts about EC2 Elastic Load Balancers in AWS <ec2_elb_facts_module>
  ec2_elb_lb - Creates or destroys Amazon ELB. <ec2_elb_lb_module>
  ec2_eni (E) - Create and optionally attach an Elastic Network Interface (ENI) to an instance <ec2_eni_module>
  ec2_eni_facts (E) - Gather facts about ec2 ENI interfaces in AWS <ec2_eni_facts_module>
  ec2_facts - Gathers facts about remote hosts within ec2 (aws) <ec2_facts_module>
  ec2_group - maintain an ec2 VPC security group. <ec2_group_module>
  ec2_key - maintain an ec2 key pair. <ec2_key_module>
  ec2_lc - Create or delete AWS Autoscaling Launch Configurations <ec2_lc_module>
  ec2_lc_find (E) - Find AWS Autoscaling Launch Configurations <ec2_lc_find_module>
  ec2_metric_alarm - Create/update or delete AWS Cloudwatch 'metric alarms' <ec2_metric_alarm_module>
  ec2_remote_facts (E) - Gather facts about ec2 instances in AWS <ec2_remote_facts_module>
  ec2_scaling_policy - Create or delete AWS scaling policies for Autoscaling groups <ec2_scaling_policy_module>
  ec2_snapshot - creates a snapshot from an existing volume <ec2_snapshot_module>
  ec2_snapshot_facts (E) - Gather facts about ec2 volume snapshots in AWS <ec2_snapshot_facts_module>
  ec2_tag - create and remove tag(s) to ec2 resources. <ec2_tag_module>
  ec2_vol - create and attach a volume, return volume id and device map <ec2_vol_module>
  ec2_vol_facts (E) - Gather facts about ec2 volumes in AWS <ec2_vol_facts_module>
  ec2_vpc - configure AWS virtual private clouds <ec2_vpc_module>
  ec2_vpc_dhcp_options (E) - Manages DHCP Options, and can ensure the DHCP options for the given VPC match what's requested <ec2_vpc_dhcp_options_module>
  ec2_vpc_dhcp_options_facts (E) - Gather facts about dhcp options sets in AWS <ec2_vpc_dhcp_options_facts_module>
  ec2_vpc_igw (E) - Manage an AWS VPC Internet gateway <ec2_vpc_igw_module>
  ec2_vpc_nacl (E) - create and delete Network ACLs. <ec2_vpc_nacl_module>
  ec2_vpc_nacl_facts (E) - Gather facts about Network ACLs in an AWS VPC <ec2_vpc_nacl_facts_module>
  ec2_vpc_nat_gateway (E) - Manage AWS VPC NAT Gateways. <ec2_vpc_nat_gateway_module>
  ec2_vpc_net - Configure AWS virtual private clouds <ec2_vpc_net_module>
  ec2_vpc_net_facts (E) - Gather facts about ec2 VPCs in AWS <ec2_vpc_net_facts_module>
  ec2_vpc_peer (E) - create, delete, accept, and reject VPC peering connections between two VPCs. <ec2_vpc_peer_module>
  ec2_vpc_route_table (E) - Manage route tables for AWS virtual private clouds <ec2_vpc_route_table_module>
  ec2_vpc_route_table_facts (E) - Gather facts about ec2 VPC route tables in AWS <ec2_vpc_route_table_facts_module>
  ec2_vpc_subnet (E) - Manage subnets in AWS virtual private clouds <ec2_vpc_subnet_module>
  ec2_vpc_subnet_facts (E) - Gather facts about ec2 VPC subnets in AWS <ec2_vpc_subnet_facts_module>
  ec2_vpc_vgw (E) - Create and delete AWS VPN Virtual Gateways. <ec2_vpc_vgw_module>
  ec2_win_password (E) - gets the default administrator password for ec2 windows instances <ec2_win_password_module>
  ecs_cluster (E) - create or terminate ecs clusters <ecs_cluster_module>
  ecs_service (E) - create, terminate, start or stop a service in ecs <ecs_service_module>
  ecs_service_facts (E) - list or describe services in ecs <ecs_service_facts_module>
  ecs_task (E) - run, start or stop a task in ecs <ecs_task_module>
  ecs_taskdefinition (E) - register a task definition in ecs <ecs_taskdefinition_module>
  efs (E) - create and maintain EFS file systems <efs_module>
  efs_facts (E) - Get information about Amazon EFS file systems <efs_facts_module>
  elasticache - Manage cache clusters in Amazon Elasticache. <elasticache_module>
  elasticache_subnet_group - manage Elasticache subnet groups <elasticache_subnet_group_module>
  execute_lambda (E) - Execute an AWS Lambda function <execute_lambda_module>
  iam - Manage IAM users, groups, roles and keys <iam_module>
  iam_cert - Manage server certificates for use on ELBs and CloudFront <iam_cert_module>
  iam_mfa_device_facts (E) - List the MFA (Multi-Factor Authentication) devices registered for a user <iam_mfa_device_facts_module>
  iam_policy - Manage IAM policies for users, groups, and roles <iam_policy_module>
  iam_server_certificate_facts (E) - Retrieve the facts of a server certificate <iam_server_certificate_facts_module>
  kinesis_stream (E) - Manage a Kinesis Stream. <kinesis_stream_module>
  lambda (E) - Manage AWS Lambda functions <lambda_module>
  lambda_alias (E) - Creates, updates or deletes AWS Lambda function aliases. <lambda_alias_module>
  lambda_event (E) - Creates, updates or deletes AWS Lambda function event mappings. <lambda_event_module>
  lambda_facts (E) - Gathers AWS Lambda function details as Ansible facts <lambda_facts_module>
  rds - create, delete, or modify an Amazon rds instance <rds_module>
  rds_param_group - manage RDS parameter groups <rds_param_group_module>
  rds_subnet_group - manage RDS database subnet groups <rds_subnet_group_module>
  redshift (E) - create, delete, or modify an Amazon Redshift instance <redshift_module>
  redshift_subnet_group (E) - mange Redshift cluster subnet groups <redshift_subnet_group_module>
  route53 - add or delete entries in Amazons Route53 DNS service <route53_module>
  route53_facts (E) - Retrieves route53 details using AWS methods <route53_facts_module>
  route53_health_check (E) - add or delete health-checks in Amazons Route53 DNS service <route53_health_check_module>
  route53_zone (E) - add or delete Route53 zones <route53_zone_module>
  s3 - manage objects in S3. <s3_module>
  s3_bucket (E) - Manage S3 buckets in AWS, Ceph, Walrus and FakeS3 <s3_bucket_module>
  s3_lifecycle (E) - Manage s3 bucket lifecycle rules in AWS <s3_lifecycle_module>
  s3_logging (E) - Manage logging facility of an s3 bucket in AWS <s3_logging_module>
  s3_website (E) - Configure an s3 bucket as a website <s3_website_module>
  sns_topic (E) - Manages AWS SNS topics and subscriptions <sns_topic_module>
  sqs_queue (E) - Creates or deletes AWS SQS queues. <sqs_queue_module>
  sts_assume_role (E) - Assume a role using AWS Security Token Service and obtain temporary credentials <sts_assume_role_module>
  sts_session_token (E) - Obtain a session token from the AWS Security Token Service <sts_session_token_module>

Atomic
------

.. toctree:: :maxdepth: 1

  atomic_host (E) - Manage the atomic host platform <atomic_host_module>
  atomic_image (E) - Manage the container images on the atomic host platform <atomic_image_module>

Azure
-----

.. toctree:: :maxdepth: 1

  azure - create or terminate a virtual machine in azure <azure_module>
  azure_rm_deployment (E) - Create or destroy Azure Resource Manager template deployments <azure_rm_deployment_module>
  azure_rm_networkinterface - Manage Azure network interfaces. <azure_rm_networkinterface_module>
  azure_rm_networkinterface_facts - Get network interface facts. <azure_rm_networkinterface_facts_module>
  azure_rm_publicipaddress - Manage Azure Public IP Addresses. <azure_rm_publicipaddress_module>
  azure_rm_publicipaddress_facts - Get public IP facts. <azure_rm_publicipaddress_facts_module>
  azure_rm_resourcegroup - Manage Azure resource groups. <azure_rm_resourcegroup_module>
  azure_rm_resourcegroup_facts - Get resource group facts. <azure_rm_resourcegroup_facts_module>
  azure_rm_securitygroup - Manage Azure network security groups. <azure_rm_securitygroup_module>
  azure_rm_securitygroup_facts - Get security group facts. <azure_rm_securitygroup_facts_module>
  azure_rm_storageaccount - Manage Azure storage accounts. <azure_rm_storageaccount_module>
  azure_rm_storageaccount_facts - Get storage account facts. <azure_rm_storageaccount_facts_module>
  azure_rm_storageblob - Manage blob containers and blob objects. <azure_rm_storageblob_module>
  azure_rm_subnet - Manage Azure subnets. <azure_rm_subnet_module>
  azure_rm_virtualmachine - Manage Azure virtual machines. <azure_rm_virtualmachine_module>
  azure_rm_virtualmachineimage_facts - Get virtual machine image facts. <azure_rm_virtualmachineimage_facts_module>
  azure_rm_virtualnetwork - Manage Azure virtual networks. <azure_rm_virtualnetwork_module>
  azure_rm_virtualnetwork_facts - Get virtual network facts. <azure_rm_virtualnetwork_facts_module>

Centurylink
-----------

.. toctree:: :maxdepth: 1

  clc_aa_policy (E) - Create or Delete Anti Affinity Policies at CenturyLink Cloud. <clc_aa_policy_module>
  clc_alert_policy (E) - Create or Delete Alert Policies at CenturyLink Cloud. <clc_alert_policy_module>
  clc_blueprint_package (E) - deploys a blue print package on a set of servers in CenturyLink Cloud. <clc_blueprint_package_module>
  clc_firewall_policy (E) - Create/delete/update firewall policies <clc_firewall_policy_module>
  clc_group (E) - Create/delete Server Groups at Centurylink Cloud <clc_group_module>
  clc_loadbalancer (E) - Create, Delete shared loadbalancers in CenturyLink Cloud. <clc_loadbalancer_module>
  clc_modify_server (E) - modify servers in CenturyLink Cloud. <clc_modify_server_module>
  clc_publicip (E) - Add and Delete public ips on servers in CenturyLink Cloud. <clc_publicip_module>
  clc_server (E) - Create, Delete, Start and Stop servers in CenturyLink Cloud. <clc_server_module>
  clc_server_snapshot (E) - Create, Delete and Restore server snapshots in CenturyLink Cloud. <clc_server_snapshot_module>

Cloudstack
----------

.. toctree:: :maxdepth: 1

  cs_account (E) - Manages accounts on Apache CloudStack based clouds. <cs_account_module>
  cs_affinitygroup (E) - Manages affinity groups on Apache CloudStack based clouds. <cs_affinitygroup_module>
  cs_cluster (E) - Manages host clusters on Apache CloudStack based clouds. <cs_cluster_module>
  cs_configuration (E) - Manages configuration on Apache CloudStack based clouds. <cs_configuration_module>
  cs_domain (E) - Manages domains on Apache CloudStack based clouds. <cs_domain_module>
  cs_facts (E) - Gather facts on instances of Apache CloudStack based clouds. <cs_facts_module>
  cs_firewall (E) - Manages firewall rules on Apache CloudStack based clouds. <cs_firewall_module>
  cs_instance (E) - Manages instances and virtual machines on Apache CloudStack based clouds. <cs_instance_module>
  cs_instance_facts (E) - Gathering facts from the API of instances from Apache CloudStack based clouds. <cs_instance_facts_module>
  cs_instancegroup (E) - Manages instance groups on Apache CloudStack based clouds. <cs_instancegroup_module>
  cs_ip_address (E) - Manages public IP address associations on Apache CloudStack based clouds. <cs_ip_address_module>
  cs_iso (E) - Manages ISO images on Apache CloudStack based clouds. <cs_iso_module>
  cs_loadbalancer_rule (E) - Manages load balancer rules on Apache CloudStack based clouds. <cs_loadbalancer_rule_module>
  cs_loadbalancer_rule_member (E) - Manages load balancer rule members on Apache CloudStack based clouds. <cs_loadbalancer_rule_member_module>
  cs_network (E) - Manages networks on Apache CloudStack based clouds. <cs_network_module>
  cs_pod (E) - Manages pods on Apache CloudStack based clouds. <cs_pod_module>
  cs_portforward (E) - Manages port forwarding rules on Apache CloudStack based clouds. <cs_portforward_module>
  cs_project (E) - Manages projects on Apache CloudStack based clouds. <cs_project_module>
  cs_resourcelimit (E) - Manages resource limits on Apache CloudStack based clouds. <cs_resourcelimit_module>
  cs_router (E) - Manages routers on Apache CloudStack based clouds. <cs_router_module>
  cs_securitygroup (E) - Manages security groups on Apache CloudStack based clouds. <cs_securitygroup_module>
  cs_securitygroup_rule (E) - Manages security group rules on Apache CloudStack based clouds. <cs_securitygroup_rule_module>
  cs_snapshot_policy (E) - Manages volume snapshot policies on Apache CloudStack based clouds. <cs_snapshot_policy_module>
  cs_sshkeypair (E) - Manages SSH keys on Apache CloudStack based clouds. <cs_sshkeypair_module>
  cs_staticnat (E) - Manages static NATs on Apache CloudStack based clouds. <cs_staticnat_module>
  cs_template (E) - Manages templates on Apache CloudStack based clouds. <cs_template_module>
  cs_user (E) - Manages users on Apache CloudStack based clouds. <cs_user_module>
  cs_vmsnapshot (E) - Manages VM snapshots on Apache CloudStack based clouds. <cs_vmsnapshot_module>
  cs_volume (E) - Manages volumes on Apache CloudStack based clouds. <cs_volume_module>
  cs_zone (E) - Manages zones on Apache CloudStack based clouds. <cs_zone_module>
  cs_zone_facts (E) - Gathering facts of zones from Apache CloudStack based clouds. <cs_zone_facts_module>

Digital Ocean
-------------

.. toctree:: :maxdepth: 1

  digital_ocean - Create/delete a droplet/SSH_key in DigitalOcean <digital_ocean_module>
  digital_ocean_block_storage - Create/destroy or attach/detach Block Storage volumes in DigitalOcean <digital_ocean_block_storage_module>
  digital_ocean_domain - Create/delete a DNS record in DigitalOcean <digital_ocean_domain_module>
  digital_ocean_sshkey - Create/delete an SSH key in DigitalOcean <digital_ocean_sshkey_module>
  digital_ocean_tag - Create and remove tag(s) to DigitalOcean resource. <digital_ocean_tag_module>

Docker
------

.. toctree:: :maxdepth: 1

  docker (D) - manage docker containers <docker_module>
  docker_container - manage docker containers <docker_container_module>
  docker_image - Manage docker images. <docker_image_module>
  docker_image_facts - Inspect docker images <docker_image_facts_module>
  docker_login - Log into a Docker registry. <docker_login_module>
  docker_network - Manage Docker networks <docker_network_module>
  docker_service - Manage docker services and containers. <docker_service_module>

Google
------

.. toctree:: :maxdepth: 1

  gc_storage - This module manages objects/buckets in Google Cloud Storage. <gc_storage_module>
  gcdns_record (E) - Creates or removes resource records in Google Cloud DNS <gcdns_record_module>
  gcdns_zone (E) - Creates or removes zones in Google Cloud DNS <gcdns_zone_module>
  gce - create or terminate GCE instances <gce_module>
  gce_img (E) - utilize GCE image resources <gce_img_module>
  gce_lb - create/destroy GCE load-balancer resources <gce_lb_module>
  gce_mig - Create, Update or Destroy a Managed Instance Group (MIG). <gce_mig_module>
  gce_net - create/destroy GCE networks and firewall rules <gce_net_module>
  gce_pd - utilize GCE persistent disk resources <gce_pd_module>
  gce_tag (E) - add or remove tag(s) to/from GCE instance <gce_tag_module>

Linode
------

.. toctree:: :maxdepth: 1

  linode - create / delete / stop / restart an instance in Linode Public Cloud <linode_module>

Lxc
---

.. toctree:: :maxdepth: 1

  lxc_container (E) - Manage LXC Containers <lxc_container_module>

Lxd
---

.. toctree:: :maxdepth: 1

  lxd_container (E) - Manage LXD Containers <lxd_container_module>
  lxd_profile (E) - Manage LXD profiles <lxd_profile_module>

Misc
----

.. toctree:: :maxdepth: 1

  ovirt (E) - oVirt/RHEV platform management <ovirt_module>
  proxmox (E) - management of instances in Proxmox VE cluster <proxmox_module>
  proxmox_template (E) - management of OS templates in Proxmox VE cluster <proxmox_template_module>
  rhevm (E) - RHEV/oVirt automation <rhevm_module>
  virt (E) - Manages virtual machines supported by libvirt <virt_module>
  virt_net (E) - Manage libvirt network configuration <virt_net_module>
  virt_pool (E) - Manage libvirt storage pools <virt_pool_module>

Openstack
---------

.. toctree:: :maxdepth: 1

  glance_image (D) - Add/Delete images from glance <glance_image_module>
  keystone_user (D) - Manage OpenStack Identity (keystone) users, tenants and roles <keystone_user_module>
  nova_compute (D) - Create/Delete VMs from OpenStack <nova_compute_module>
  nova_keypair (D) - Add/Delete key pair from nova <nova_keypair_module>
  os_auth - Retrieve an auth token <os_auth_module>
  os_client_config - Get OpenStack Client config <os_client_config_module>
  os_flavor_facts (E) - Retrieve facts about one or more flavors <os_flavor_facts_module>
  os_floating_ip - Add/Remove floating IP from an instance <os_floating_ip_module>
  os_group (E) - Manage OpenStack Identity Groups <os_group_module>
  os_image - Add/Delete images from OpenStack Cloud <os_image_module>
  os_image_facts - Retrieve facts about an image within OpenStack. <os_image_facts_module>
  os_ironic - Create/Delete Bare Metal Resources from OpenStack <os_ironic_module>
  os_ironic_inspect (E) - Explicitly triggers baremetal node introspection in ironic. <os_ironic_inspect_module>
  os_ironic_node - Activate/Deactivate Bare Metal Resources from OpenStack <os_ironic_node_module>
  os_keypair - Add/Delete a keypair from OpenStack <os_keypair_module>
  os_keystone_domain (E) - Manage OpenStack Identity Domains <os_keystone_domain_module>
  os_keystone_domain_facts (E) - Retrieve facts about one or more OpenStack domains <os_keystone_domain_facts_module>
  os_keystone_role (E) - Manage OpenStack Identity Roles <os_keystone_role_module>
  os_keystone_service (E) - Manage OpenStack Identity services <os_keystone_service_module>
  os_network - Creates/removes networks from OpenStack <os_network_module>
  os_networks_facts - Retrieve facts about one or more OpenStack networks. <os_networks_facts_module>
  os_nova_flavor - Manage OpenStack compute flavors <os_nova_flavor_module>
  os_object - Create or Delete objects and containers from OpenStack <os_object_module>
  os_port - Add/Update/Delete ports from an OpenStack cloud. <os_port_module>
  os_port_facts (E) - Retrieve facts about ports within OpenStack. <os_port_facts_module>
  os_project (E) - Manage OpenStack Projects <os_project_module>
  os_project_facts (E) - Retrieve facts about one or more OpenStack projects <os_project_facts_module>
  os_recordset (E) - Manage OpenStack DNS recordsets <os_recordset_module>
  os_router - Create or delete routers from OpenStack <os_router_module>
  os_security_group - Add/Delete security groups from an OpenStack cloud. <os_security_group_module>
  os_security_group_rule - Add/Delete rule from an existing security group <os_security_group_rule_module>
  os_server - Create/Delete Compute Instances from OpenStack <os_server_module>
  os_server_actions - Perform actions on Compute Instances from OpenStack <os_server_actions_module>
  os_server_facts - Retrieve facts about one or more compute instances <os_server_facts_module>
  os_server_group (E) - Manage OpenStack server groups <os_server_group_module>
  os_server_volume - Attach/Detach Volumes from OpenStack VM's <os_server_volume_module>
  os_stack (E) - Add/Remove Heat Stack <os_stack_module>
  os_subnet - Add/Remove subnet to an OpenStack network <os_subnet_module>
  os_subnets_facts - Retrieve facts about one or more OpenStack subnets. <os_subnets_facts_module>
  os_user - Manage OpenStack Identity Users <os_user_module>
  os_user_facts (E) - Retrieve facts about one or more OpenStack users <os_user_facts_module>
  os_user_group - Associate OpenStack Identity users and groups <os_user_group_module>
  os_user_role (E) - Associate OpenStack Identity users and roles <os_user_role_module>
  os_volume - Create/Delete Cinder Volumes <os_volume_module>
  os_zone (E) - Manage OpenStack DNS zones <os_zone_module>
  quantum_floating_ip (D) - Add/Remove floating IP from an instance <quantum_floating_ip_module>
  quantum_floating_ip_associate (D) - Associate or disassociate a particular floating IP with an instance <quantum_floating_ip_associate_module>
  quantum_network (D) - Creates/Removes networks from OpenStack <quantum_network_module>
  quantum_router (D) - Create or Remove router from openstack <quantum_router_module>
  quantum_router_gateway (D) - set/unset a gateway interface for the router with the specified external network <quantum_router_gateway_module>
  quantum_router_interface (D) - Attach/Detach a subnet's interface to a router <quantum_router_interface_module>
  quantum_subnet (D) - Add/remove subnet from a network <quantum_subnet_module>

Ovh
---

.. toctree:: :maxdepth: 1

  ovh_ip_loadbalancing_backend (E) - Manage OVH IP LoadBalancing backends <ovh_ip_loadbalancing_backend_module>

Ovirt
-----

.. toctree:: :maxdepth: 1

  ovirt_auth (E) - Module to manage authentication to oVirt. <ovirt_auth_module>
  ovirt_disks (E) - Module to manage Virtual Machine and floating disks in oVirt. <ovirt_disks_module>
  ovirt_vms (E) - Module to manage Virtual Machines in oVirt. <ovirt_vms_module>

Profitbricks
------------

.. toctree:: :maxdepth: 1

  profitbricks (E) - Create, destroy, start, stop, and reboot a ProfitBricks virtual machine. <profitbricks_module>
  profitbricks_datacenter (E) - Create or destroy a ProfitBricks Virtual Datacenter. <profitbricks_datacenter_module>
  profitbricks_nic (E) - Create or Remove a NIC. <profitbricks_nic_module>
  profitbricks_volume (E) - Create or destroy a volume. <profitbricks_volume_module>
  profitbricks_volume_attachments (E) - Attach or detach a volume. <profitbricks_volume_attachments_module>

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
  rax_clb_ssl (E) - Manage SSL termination for a Rackspace Cloud Load Balancer. <rax_clb_ssl_module>
  rax_dns - Manage domains on Rackspace Cloud DNS <rax_dns_module>
  rax_dns_record - Manage DNS records on Rackspace Cloud DNS <rax_dns_record_module>
  rax_facts - Gather facts for Rackspace Cloud Servers <rax_facts_module>
  rax_files - Manipulate Rackspace Cloud Files Containers <rax_files_module>
  rax_files_objects - Upload, download, and delete objects in Rackspace Cloud Files <rax_files_objects_module>
  rax_identity - Load Rackspace Cloud Identity <rax_identity_module>
  rax_keypair - Create a keypair for use with Rackspace Cloud Servers <rax_keypair_module>
  rax_meta - Manipulate metadata for Rackspace Cloud Servers <rax_meta_module>
  rax_mon_alarm (E) - Create or delete a Rackspace Cloud Monitoring alarm. <rax_mon_alarm_module>
  rax_mon_check (E) - Create or delete a Rackspace Cloud Monitoring check for an existing entity. <rax_mon_check_module>
  rax_mon_entity (E) - Create or delete a Rackspace Cloud Monitoring entity <rax_mon_entity_module>
  rax_mon_notification (E) - Create or delete a Rackspace Cloud Monitoring notification. <rax_mon_notification_module>
  rax_mon_notification_plan (E) - Create or delete a Rackspace Cloud Monitoring notification plan. <rax_mon_notification_plan_module>
  rax_network - create / delete an isolated network in Rackspace Public Cloud <rax_network_module>
  rax_queue - create / delete a queue in Rackspace Public Cloud <rax_queue_module>
  rax_scaling_group - Manipulate Rackspace Cloud Autoscale Groups <rax_scaling_group_module>
  rax_scaling_policy - Manipulate Rackspace Cloud Autoscale Scaling Policy <rax_scaling_policy_module>

Smartos
-------

.. toctree:: :maxdepth: 1

  smartos_image_facts (E) - Get SmartOS image details. <smartos_image_facts_module>

Softlayer
---------

.. toctree:: :maxdepth: 1

  sl_vm (E) - create or cancel a virtual instance in SoftLayer <sl_vm_module>

Vmware
------

.. toctree:: :maxdepth: 1

  vca_fw (E) - add remove firewall rules in a gateway  in a vca <vca_fw_module>
  vca_nat (E) - add remove nat rules in a gateway  in a vca <vca_nat_module>
  vca_vapp (E) - Manages vCloud Air vApp instances. <vca_vapp_module>
  vmware_cluster (E) - Create VMware vSphere Cluster <vmware_cluster_module>
  vmware_datacenter (E) - Manage VMware vSphere Datacenters <vmware_datacenter_module>
  vmware_dns_config (E) - Manage VMware ESXi DNS Configuration <vmware_dns_config_module>
  vmware_dvs_host (E) - Add or remove a host from distributed virtual switch <vmware_dvs_host_module>
  vmware_dvs_portgroup (E) - Create or remove a Distributed vSwitch portgroup <vmware_dvs_portgroup_module>
  vmware_dvswitch (E) - Create or remove a distributed vSwitch <vmware_dvswitch_module>
  vmware_guest (E) - Manages virtualmachines in vcenter <vmware_guest_module>
  vmware_host (E) - Add/remove ESXi host to/from vCenter <vmware_host_module>
  vmware_local_user_manager (E) - Manage local users on an ESXi host <vmware_local_user_manager_module>
  vmware_maintenancemode (E) - Place a host into maintenance mode <vmware_maintenancemode_module>
  vmware_migrate_vmk (E) - Migrate a VMK interface from VSS to VDS <vmware_migrate_vmk_module>
  vmware_portgroup (E) - Create a VMware portgroup <vmware_portgroup_module>
  vmware_target_canonical_facts (E) - Return canonical (NAA) from an ESXi host <vmware_target_canonical_facts_module>
  vmware_vm_facts (E) - Return basic facts pertaining to a vSphere virtual machine guest <vmware_vm_facts_module>
  vmware_vm_shell (E) - Execute a process in VM <vmware_vm_shell_module>
  vmware_vm_vss_dvs_migrate (E) - Migrates a virtual machine from a standard vswitch to distributed <vmware_vm_vss_dvs_migrate_module>
  vmware_vmkernel (E) - Create a VMware VMkernel Interface <vmware_vmkernel_module>
  vmware_vmkernel_ip_config (E) - Configure the VMkernel IP Address <vmware_vmkernel_ip_config_module>
  vmware_vmotion (E) - Move a virtual machine using vMotion <vmware_vmotion_module>
  vmware_vsan_cluster (E) - Configure VSAN clustering on an ESXi host <vmware_vsan_cluster_module>
  vmware_vswitch (E) - Add a VMware Standard Switch to an ESXi host <vmware_vswitch_module>
  vsphere_copy (E) - Copy a file to a vCenter datastore <vsphere_copy_module>
  vsphere_guest - Create/delete/manage a guest VM through VMware vSphere. <vsphere_guest_module>

Webfaction
----------

.. toctree:: :maxdepth: 1

  webfaction_app (E) - Add or remove applications on a Webfaction host <webfaction_app_module>
  webfaction_db (E) - Add or remove a database on Webfaction <webfaction_db_module>
  webfaction_domain (E) - Add or remove domains and subdomains on Webfaction <webfaction_domain_module>
  webfaction_mailbox (E) - Add or remove mailboxes on Webfaction <webfaction_mailbox_module>
  webfaction_site (E) - Add or remove a website on a Webfaction host <webfaction_site_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
