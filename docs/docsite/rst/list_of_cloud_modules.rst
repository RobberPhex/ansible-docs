Cloud Modules
`````````````

.. toctree:: :maxdepth: 1


Amazon
------

.. toctree:: :maxdepth: 1

  aws_kms - Perform various KMS management tasks. <aws_kms_module>
  cloudformation - Create or delete an AWS CloudFormation stack <cloudformation_module>
  cloudformation_facts - Obtain facts about an AWS CloudFormation stack <cloudformation_facts_module>
  cloudfront_facts - Obtain facts about an AWS CloudFront distribution <cloudfront_facts_module>
  cloudtrail - manage CloudTrail creation and deletion <cloudtrail_module>
  cloudwatchevent_rule - Manage CloudWatch Event rules and targets <cloudwatchevent_rule_module>
  dynamodb_table - Create, update or delete AWS Dynamo DB tables. <dynamodb_table_module>
  ec2 - create, terminate, start or stop an instance in ec2 <ec2_module>
  ec2_ami - create or destroy an image in ec2 <ec2_ami_module>
  ec2_ami_copy - copies AMI between AWS regions, return new image id <ec2_ami_copy_module>
  ec2_ami_find - Searches for AMIs to obtain the AMI ID and other information <ec2_ami_find_module>
  ec2_ami_search (D) - Retrieve AWS AMI information for a given operating system. <ec2_ami_search_module>
  ec2_asg - Create or delete AWS Autoscaling Groups <ec2_asg_module>
  ec2_asg_facts - Gather facts about ec2 Auto Scaling Groups (ASGs) in AWS <ec2_asg_facts_module>
  ec2_customer_gateway - Manage an AWS customer gateway <ec2_customer_gateway_module>
  ec2_eip - manages EC2 elastic IP (EIP) addresses. <ec2_eip_module>
  ec2_elb - De-registers or registers instances from EC2 ELBs <ec2_elb_module>
  ec2_elb_facts - Gather facts about EC2 Elastic Load Balancers in AWS <ec2_elb_facts_module>
  ec2_elb_lb - Creates or destroys Amazon ELB. <ec2_elb_lb_module>
  ec2_eni - Create and optionally attach an Elastic Network Interface (ENI) to an instance <ec2_eni_module>
  ec2_eni_facts - Gather facts about ec2 ENI interfaces in AWS <ec2_eni_facts_module>
  ec2_facts - Gathers facts about remote hosts within ec2 (aws) <ec2_facts_module>
  ec2_group - maintain an ec2 VPC security group. <ec2_group_module>
  ec2_group_facts - Gather facts about ec2 security groups in AWS. <ec2_group_facts_module>
  ec2_key - maintain an ec2 key pair. <ec2_key_module>
  ec2_lc - Create or delete AWS Autoscaling Launch Configurations <ec2_lc_module>
  ec2_lc_facts - Gather facts about AWS Autoscaling Launch Configurations <ec2_lc_facts_module>
  ec2_lc_find - Find AWS Autoscaling Launch Configurations <ec2_lc_find_module>
  ec2_metric_alarm - Create/update or delete AWS Cloudwatch 'metric alarms' <ec2_metric_alarm_module>
  ec2_remote_facts - Gather facts about ec2 instances in AWS <ec2_remote_facts_module>
  ec2_scaling_policy - Create or delete AWS scaling policies for Autoscaling groups <ec2_scaling_policy_module>
  ec2_snapshot - creates a snapshot from an existing volume <ec2_snapshot_module>
  ec2_snapshot_facts - Gather facts about ec2 volume snapshots in AWS <ec2_snapshot_facts_module>
  ec2_tag - create and remove tag(s) to ec2 resources. <ec2_tag_module>
  ec2_vol - create and attach a volume, return volume id and device map <ec2_vol_module>
  ec2_vol_facts - Gather facts about ec2 volumes in AWS <ec2_vol_facts_module>
  ec2_vpc (D) - configure AWS virtual private clouds <ec2_vpc_module>
  ec2_vpc_dhcp_options - Manages DHCP Options, and can ensure the DHCP options for the given VPC match what's requested <ec2_vpc_dhcp_options_module>
  ec2_vpc_dhcp_options_facts - Gather facts about dhcp options sets in AWS <ec2_vpc_dhcp_options_facts_module>
  ec2_vpc_igw - Manage an AWS VPC Internet gateway <ec2_vpc_igw_module>
  ec2_vpc_igw_facts - Gather facts about internet gateways in AWS <ec2_vpc_igw_facts_module>
  ec2_vpc_nacl - create and delete Network ACLs. <ec2_vpc_nacl_module>
  ec2_vpc_nacl_facts - Gather facts about Network ACLs in an AWS VPC <ec2_vpc_nacl_facts_module>
  ec2_vpc_nat_gateway - Manage AWS VPC NAT Gateways. <ec2_vpc_nat_gateway_module>
  ec2_vpc_nat_gateway_facts - Retrieves AWS VPC Managed Nat Gateway details using AWS methods. <ec2_vpc_nat_gateway_facts_module>
  ec2_vpc_net - Configure AWS virtual private clouds <ec2_vpc_net_module>
  ec2_vpc_net_facts - Gather facts about ec2 VPCs in AWS <ec2_vpc_net_facts_module>
  ec2_vpc_peer - create, delete, accept, and reject VPC peering connections between two VPCs. <ec2_vpc_peer_module>
  ec2_vpc_route_table - Manage route tables for AWS virtual private clouds <ec2_vpc_route_table_module>
  ec2_vpc_route_table_facts - Gather facts about ec2 VPC route tables in AWS <ec2_vpc_route_table_facts_module>
  ec2_vpc_subnet - Manage subnets in AWS virtual private clouds <ec2_vpc_subnet_module>
  ec2_vpc_subnet_facts - Gather facts about ec2 VPC subnets in AWS <ec2_vpc_subnet_facts_module>
  ec2_vpc_vgw - Create and delete AWS VPN Virtual Gateways. <ec2_vpc_vgw_module>
  ec2_vpc_vgw_facts - Gather facts about virtual gateways in AWS <ec2_vpc_vgw_facts_module>
  ec2_win_password - gets the default administrator password for ec2 windows instances <ec2_win_password_module>
  ecs_cluster - create or terminate ecs clusters <ecs_cluster_module>
  ecs_ecr - Manage Elastic Container Registry repositories <ecs_ecr_module>
  ecs_service - create, terminate, start or stop a service in ecs <ecs_service_module>
  ecs_service_facts - list or describe services in ecs <ecs_service_facts_module>
  ecs_task - run, start or stop a task in ecs <ecs_task_module>
  ecs_taskdefinition - register a task definition in ecs <ecs_taskdefinition_module>
  efs - create and maintain EFS file systems <efs_module>
  efs_facts - Get information about Amazon EFS file systems <efs_facts_module>
  elasticache - Manage cache clusters in Amazon Elasticache. <elasticache_module>
  elasticache_parameter_group - Manage cache security groups in Amazon Elasticache. <elasticache_parameter_group_module>
  elasticache_snapshot - Manage cache snapshots in Amazon Elasticache. <elasticache_snapshot_module>
  elasticache_subnet_group - manage Elasticache subnet groups <elasticache_subnet_group_module>
  execute_lambda - Execute an AWS Lambda function <execute_lambda_module>
  iam - Manage IAM users, groups, roles and keys <iam_module>
  iam_cert - Manage server certificates for use on ELBs and CloudFront <iam_cert_module>
  iam_mfa_device_facts - List the MFA (Multi-Factor Authentication) devices registered for a user <iam_mfa_device_facts_module>
  iam_policy - Manage IAM policies for users, groups, and roles <iam_policy_module>
  iam_role - Manage AWS IAM roles <iam_role_module>
  iam_server_certificate_facts - Retrieve the facts of a server certificate <iam_server_certificate_facts_module>
  kinesis_stream - Manage a Kinesis Stream. <kinesis_stream_module>
  lambda - Manage AWS Lambda functions <lambda_module>
  lambda_alias - Creates, updates or deletes AWS Lambda function aliases. <lambda_alias_module>
  lambda_event - Creates, updates or deletes AWS Lambda function event mappings. <lambda_event_module>
  lambda_facts - Gathers AWS Lambda function details as Ansible facts <lambda_facts_module>
  rds - create, delete, or modify an Amazon rds instance <rds_module>
  rds_param_group - manage RDS parameter groups <rds_param_group_module>
  rds_subnet_group - manage RDS database subnet groups <rds_subnet_group_module>
  redshift - create, delete, or modify an Amazon Redshift instance <redshift_module>
  redshift_subnet_group - mange Redshift cluster subnet groups <redshift_subnet_group_module>
  route53 - add or delete entries in Amazons Route53 DNS service <route53_module>
  route53_facts - Retrieves route53 details using AWS methods <route53_facts_module>
  route53_health_check - add or delete health-checks in Amazons Route53 DNS service <route53_health_check_module>
  route53_zone - add or delete Route53 zones <route53_zone_module>
  s3 - manage objects in S3. <s3_module>
  s3_bucket - Manage S3 buckets in AWS, Ceph, Walrus and FakeS3 <s3_bucket_module>
  s3_lifecycle - Manage s3 bucket lifecycle rules in AWS <s3_lifecycle_module>
  s3_logging - Manage logging facility of an s3 bucket in AWS <s3_logging_module>
  s3_sync - Efficiently upload multiple files to S3 <s3_sync_module>
  s3_website - Configure an s3 bucket as a website <s3_website_module>
  sns_topic - Manages AWS SNS topics and subscriptions <sns_topic_module>
  sqs_queue - Creates or deletes AWS SQS queues. <sqs_queue_module>
  sts_assume_role - Assume a role using AWS Security Token Service and obtain temporary credentials <sts_assume_role_module>
  sts_session_token - Obtain a session token from the AWS Security Token Service <sts_session_token_module>

Atomic
------

.. toctree:: :maxdepth: 1

  atomic_host - Manage the atomic host platform <atomic_host_module>
  atomic_image - Manage the container images on the atomic host platform <atomic_image_module>

Azure
-----

.. toctree:: :maxdepth: 1

  azure - create or terminate a virtual machine in azure <azure_module>
  azure_rm_deployment - Create or destroy Azure Resource Manager template deployments <azure_rm_deployment_module>
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

  clc_aa_policy - Create or Delete Anti Affinity Policies at CenturyLink Cloud. <clc_aa_policy_module>
  clc_alert_policy - Create or Delete Alert Policies at CenturyLink Cloud. <clc_alert_policy_module>
  clc_blueprint_package - deploys a blue print package on a set of servers in CenturyLink Cloud. <clc_blueprint_package_module>
  clc_firewall_policy - Create/delete/update firewall policies <clc_firewall_policy_module>
  clc_group - Create/delete Server Groups at Centurylink Cloud <clc_group_module>
  clc_loadbalancer - Create, Delete shared loadbalancers in CenturyLink Cloud. <clc_loadbalancer_module>
  clc_modify_server - modify servers in CenturyLink Cloud. <clc_modify_server_module>
  clc_publicip - Add and Delete public ips on servers in CenturyLink Cloud. <clc_publicip_module>
  clc_server - Create, Delete, Start and Stop servers in CenturyLink Cloud. <clc_server_module>
  clc_server_snapshot - Create, Delete and Restore server snapshots in CenturyLink Cloud. <clc_server_snapshot_module>

Cloudscale
----------

.. toctree:: :maxdepth: 1

  cloudscale_server - Manages servers on the cloudscale.ch IaaS service <cloudscale_server_module>

Cloudstack
----------

.. toctree:: :maxdepth: 1

  cs_account - Manages accounts on Apache CloudStack based clouds. <cs_account_module>
  cs_affinitygroup - Manages affinity groups on Apache CloudStack based clouds. <cs_affinitygroup_module>
  cs_cluster - Manages host clusters on Apache CloudStack based clouds. <cs_cluster_module>
  cs_configuration - Manages configuration on Apache CloudStack based clouds. <cs_configuration_module>
  cs_domain - Manages domains on Apache CloudStack based clouds. <cs_domain_module>
  cs_facts - Gather facts on instances of Apache CloudStack based clouds. <cs_facts_module>
  cs_firewall - Manages firewall rules on Apache CloudStack based clouds. <cs_firewall_module>
  cs_host - Manages hosts on Apache CloudStack based clouds. <cs_host_module>
  cs_instance - Manages instances and virtual machines on Apache CloudStack based clouds. <cs_instance_module>
  cs_instance_facts - Gathering facts from the API of instances from Apache CloudStack based clouds. <cs_instance_facts_module>
  cs_instancegroup - Manages instance groups on Apache CloudStack based clouds. <cs_instancegroup_module>
  cs_ip_address - Manages public IP address associations on Apache CloudStack based clouds. <cs_ip_address_module>
  cs_iso - Manages ISO images on Apache CloudStack based clouds. <cs_iso_module>
  cs_loadbalancer_rule - Manages load balancer rules on Apache CloudStack based clouds. <cs_loadbalancer_rule_module>
  cs_loadbalancer_rule_member - Manages load balancer rule members on Apache CloudStack based clouds. <cs_loadbalancer_rule_member_module>
  cs_network - Manages networks on Apache CloudStack based clouds. <cs_network_module>
  cs_nic - Manages NICs and secondary IPs of an instance on Apache CloudStack based clouds. <cs_nic_module>
  cs_pod - Manages pods on Apache CloudStack based clouds. <cs_pod_module>
  cs_portforward - Manages port forwarding rules on Apache CloudStack based clouds. <cs_portforward_module>
  cs_project - Manages projects on Apache CloudStack based clouds. <cs_project_module>
  cs_region - Manages regions on Apache CloudStack based clouds. <cs_region_module>
  cs_resourcelimit - Manages resource limits on Apache CloudStack based clouds. <cs_resourcelimit_module>
  cs_role - Manages user roles on Apache CloudStack based clouds. <cs_role_module>
  cs_router - Manages routers on Apache CloudStack based clouds. <cs_router_module>
  cs_securitygroup - Manages security groups on Apache CloudStack based clouds. <cs_securitygroup_module>
  cs_securitygroup_rule - Manages security group rules on Apache CloudStack based clouds. <cs_securitygroup_rule_module>
  cs_snapshot_policy - Manages volume snapshot policies on Apache CloudStack based clouds. <cs_snapshot_policy_module>
  cs_sshkeypair - Manages SSH keys on Apache CloudStack based clouds. <cs_sshkeypair_module>
  cs_staticnat - Manages static NATs on Apache CloudStack based clouds. <cs_staticnat_module>
  cs_template - Manages templates on Apache CloudStack based clouds. <cs_template_module>
  cs_user - Manages users on Apache CloudStack based clouds. <cs_user_module>
  cs_vmsnapshot - Manages VM snapshots on Apache CloudStack based clouds. <cs_vmsnapshot_module>
  cs_volume - Manages volumes on Apache CloudStack based clouds. <cs_volume_module>
  cs_vpc - Manages VPCs on Apache CloudStack based clouds. <cs_vpc_module>
  cs_zone - Manages zones on Apache CloudStack based clouds. <cs_zone_module>
  cs_zone_facts - Gathering facts of zones from Apache CloudStack based clouds. <cs_zone_facts_module>

Digital Ocean
-------------

.. toctree:: :maxdepth: 1

  digital_ocean - Create/delete a droplet/SSH_key in DigitalOcean <digital_ocean_module>
  digital_ocean_block_storage - Create/destroy or attach/detach Block Storage volumes in DigitalOcean <digital_ocean_block_storage_module>
  digital_ocean_domain - Create/delete a DNS record in DigitalOcean <digital_ocean_domain_module>
  digital_ocean_sshkey - Create/delete an SSH key in DigitalOcean <digital_ocean_sshkey_module>
  digital_ocean_tag - Create and remove tag(s) to DigitalOcean resource. <digital_ocean_tag_module>

Dimensiondata
-------------

.. toctree:: :maxdepth: 1

  dimensiondata_network - Create, update, and delete MCP 1.0 & 2.0 networks <dimensiondata_network_module>

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
  gcdns_record - Creates or removes resource records in Google Cloud DNS <gcdns_record_module>
  gcdns_zone - Creates or removes zones in Google Cloud DNS <gcdns_zone_module>
  gce - create or terminate GCE instances <gce_module>
  gce_eip - Create or Destroy Global or Regional External IP addresses. <gce_eip_module>
  gce_img - utilize GCE image resources <gce_img_module>
  gce_instance_template - create or destroy intance templates of Compute Engine of GCP. <gce_instance_template_module>
  gce_lb - create/destroy GCE load-balancer resources <gce_lb_module>
  gce_mig - Create, Update or Destroy a Managed Instance Group (MIG). <gce_mig_module>
  gce_net - create/destroy GCE networks and firewall rules <gce_net_module>
  gce_pd - utilize GCE persistent disk resources <gce_pd_module>
  gce_snapshot - Create or destroy snapshots for GCE storage volumes <gce_snapshot_module>
  gce_tag - add or remove tag(s) to/from GCE instances <gce_tag_module>
  gcpubsub - Create and Delete Topics/Subscriptions, Publish and pull messages on PubSub. <gcpubsub_module>
  gcpubsub_facts - List Topics/Subscriptions and Messages from Google PubSub. <gcpubsub_facts_module>
  gcspanner - Create and Delete Instances/Databases on Spanner. <gcspanner_module>

Linode
------

.. toctree:: :maxdepth: 1

  linode - create / delete / stop / restart an instance in Linode Public Cloud <linode_module>

Lxc
---

.. toctree:: :maxdepth: 1

  lxc_container - Manage LXC Containers <lxc_container_module>

Lxd
---

.. toctree:: :maxdepth: 1

  lxd_container - Manage LXD Containers <lxd_container_module>
  lxd_profile - Manage LXD profiles <lxd_profile_module>

Misc
----

.. toctree:: :maxdepth: 1

  ovirt - oVirt/RHEV platform management <ovirt_module>
  proxmox - management of instances in Proxmox VE cluster <proxmox_module>
  proxmox_kvm - Management of Qemu(KVM) Virtual Machines in Proxmox VE cluster. <proxmox_kvm_module>
  proxmox_template - management of OS templates in Proxmox VE cluster <proxmox_template_module>
  rhevm - RHEV/oVirt automation <rhevm_module>
  serverless - Manages a Serverless Framework project <serverless_module>
  virt - Manages virtual machines supported by libvirt <virt_module>
  virt_net - Manage libvirt network configuration <virt_net_module>
  virt_pool - Manage libvirt storage pools <virt_pool_module>
  xenserver_facts - get facts reported on xenserver <xenserver_facts_module>

Openstack
---------

.. toctree:: :maxdepth: 1

  glance_image (D) - Add/Delete images from glance <glance_image_module>
  keystone_user (D) - Manage OpenStack Identity (keystone) users, tenants and roles <keystone_user_module>
  nova_compute (D) - Create/Delete VMs from OpenStack <nova_compute_module>
  nova_keypair (D) - Add/Delete key pair from nova <nova_keypair_module>
  os_auth - Retrieve an auth token <os_auth_module>
  os_client_config - Get OpenStack Client config <os_client_config_module>
  os_flavor_facts - Retrieve facts about one or more flavors <os_flavor_facts_module>
  os_floating_ip - Add/Remove floating IP from an instance <os_floating_ip_module>
  os_group - Manage OpenStack Identity Groups <os_group_module>
  os_image - Add/Delete images from OpenStack Cloud <os_image_module>
  os_image_facts - Retrieve facts about an image within OpenStack. <os_image_facts_module>
  os_ironic - Create/Delete Bare Metal Resources from OpenStack <os_ironic_module>
  os_ironic_inspect - Explicitly triggers baremetal node introspection in ironic. <os_ironic_inspect_module>
  os_ironic_node - Activate/Deactivate Bare Metal Resources from OpenStack <os_ironic_node_module>
  os_keypair - Add/Delete a keypair from OpenStack <os_keypair_module>
  os_keystone_domain - Manage OpenStack Identity Domains <os_keystone_domain_module>
  os_keystone_domain_facts - Retrieve facts about one or more OpenStack domains <os_keystone_domain_facts_module>
  os_keystone_role - Manage OpenStack Identity Roles <os_keystone_role_module>
  os_keystone_service - Manage OpenStack Identity services <os_keystone_service_module>
  os_network - Creates/removes networks from OpenStack <os_network_module>
  os_networks_facts - Retrieve facts about one or more OpenStack networks. <os_networks_facts_module>
  os_nova_flavor - Manage OpenStack compute flavors <os_nova_flavor_module>
  os_nova_host_aggregate - Manage OpenStack host aggregates <os_nova_host_aggregate_module>
  os_object - Create or Delete objects and containers from OpenStack <os_object_module>
  os_port - Add/Update/Delete ports from an OpenStack cloud. <os_port_module>
  os_port_facts - Retrieve facts about ports within OpenStack. <os_port_facts_module>
  os_project - Manage OpenStack Projects <os_project_module>
  os_project_facts - Retrieve facts about one or more OpenStack projects <os_project_facts_module>
  os_quota - Manage OpenStack Quotas <os_quota_module>
  os_recordset - Manage OpenStack DNS recordsets <os_recordset_module>
  os_router - Create or delete routers from OpenStack <os_router_module>
  os_security_group - Add/Delete security groups from an OpenStack cloud. <os_security_group_module>
  os_security_group_rule - Add/Delete rule from an existing security group <os_security_group_rule_module>
  os_server - Create/Delete Compute Instances from OpenStack <os_server_module>
  os_server_actions - Perform actions on Compute Instances from OpenStack <os_server_actions_module>
  os_server_facts - Retrieve facts about one or more compute instances <os_server_facts_module>
  os_server_group - Manage OpenStack server groups <os_server_group_module>
  os_server_volume - Attach/Detach Volumes from OpenStack VM's <os_server_volume_module>
  os_stack - Add/Remove Heat Stack <os_stack_module>
  os_subnet - Add/Remove subnet to an OpenStack network <os_subnet_module>
  os_subnets_facts - Retrieve facts about one or more OpenStack subnets. <os_subnets_facts_module>
  os_user - Manage OpenStack Identity Users <os_user_module>
  os_user_facts - Retrieve facts about one or more OpenStack users <os_user_facts_module>
  os_user_group - Associate OpenStack Identity users and groups <os_user_group_module>
  os_user_role - Associate OpenStack Identity users and roles <os_user_role_module>
  os_volume - Create/Delete Cinder Volumes <os_volume_module>
  os_zone - Manage OpenStack DNS zones <os_zone_module>
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

  ovh_ip_loadbalancing_backend - Manage OVH IP LoadBalancing backends <ovh_ip_loadbalancing_backend_module>

Ovirt
-----

.. toctree:: :maxdepth: 1

  ovirt_affinity_groups - Module to manage affinity groups in oVirt <ovirt_affinity_groups_module>
  ovirt_affinity_labels - Module to manage affinity labels in oVirt <ovirt_affinity_labels_module>
  ovirt_affinity_labels_facts - Retrieve facts about one or more oVirt affinity labels <ovirt_affinity_labels_facts_module>
  ovirt_auth - Module to manage authentication to oVirt <ovirt_auth_module>
  ovirt_clusters - Module to manage clusters in oVirt <ovirt_clusters_module>
  ovirt_clusters_facts - Retrieve facts about one or more oVirt clusters <ovirt_clusters_facts_module>
  ovirt_datacenters - Module to manage data centers in oVirt <ovirt_datacenters_module>
  ovirt_datacenters_facts - Retrieve facts about one or more oVirt datacenters <ovirt_datacenters_facts_module>
  ovirt_disks - Module to manage Virtual Machine and floating disks in oVirt <ovirt_disks_module>
  ovirt_external_providers - Module to manage external providers in oVirt <ovirt_external_providers_module>
  ovirt_external_providers_facts - Retrieve facts about one or more oVirt external providers <ovirt_external_providers_facts_module>
  ovirt_groups - Module to manage groups in oVirt <ovirt_groups_module>
  ovirt_groups_facts - Retrieve facts about one or more oVirt groups <ovirt_groups_facts_module>
  ovirt_host_networks - Module to manage host networks in oVirt <ovirt_host_networks_module>
  ovirt_host_pm - Module to manage power management of hosts in oVirt <ovirt_host_pm_module>
  ovirt_hosts - Module to manage hosts in oVirt <ovirt_hosts_module>
  ovirt_hosts_facts - Retrieve facts about one or more oVirt hosts <ovirt_hosts_facts_module>
  ovirt_mac_pools - Module to manage MAC pools in oVirt <ovirt_mac_pools_module>
  ovirt_networks - Module to manage logical networks in oVirt <ovirt_networks_module>
  ovirt_networks_facts - Retrieve facts about one or more oVirt networks <ovirt_networks_facts_module>
  ovirt_nics - Module to manage network interfaces of Virtual Machines in oVirt <ovirt_nics_module>
  ovirt_nics_facts - Retrieve facts about one or more oVirt virtual machine network interfaces <ovirt_nics_facts_module>
  ovirt_permissions - Module to manage permissions of users/groups in oVirt <ovirt_permissions_module>
  ovirt_permissions_facts - Retrieve facts about one or more oVirt permissions <ovirt_permissions_facts_module>
  ovirt_quotas - Module to manage datacenter quotas in oVirt <ovirt_quotas_module>
  ovirt_quotas_facts - Retrieve facts about one or more oVirt quotas <ovirt_quotas_facts_module>
  ovirt_snapshots - Module to manage Virtual Machine Snapshots in oVirt <ovirt_snapshots_module>
  ovirt_snapshots_facts - Retrieve facts about one or more oVirt virtual machine snapshots <ovirt_snapshots_facts_module>
  ovirt_storage_domains - Module to manage storage domains in oVirt <ovirt_storage_domains_module>
  ovirt_storage_domains_facts - Retrieve facts about one or more oVirt storage domains <ovirt_storage_domains_facts_module>
  ovirt_tags - Module to manage tags in oVirt <ovirt_tags_module>
  ovirt_tags_facts - Retrieve facts about one or more oVirt tags <ovirt_tags_facts_module>
  ovirt_templates - Module to manage virtual machine templates in oVirt <ovirt_templates_module>
  ovirt_templates_facts - Retrieve facts about one or more oVirt templates <ovirt_templates_facts_module>
  ovirt_users - Module to manage users in oVirt <ovirt_users_module>
  ovirt_users_facts - Retrieve facts about one or more oVirt users <ovirt_users_facts_module>
  ovirt_vmpools - Module to manage VM pools in oVirt <ovirt_vmpools_module>
  ovirt_vmpools_facts - Retrieve facts about one or more oVirt vmpools <ovirt_vmpools_facts_module>
  ovirt_vms - Module to manage Virtual Machines in oVirt <ovirt_vms_module>
  ovirt_vms_facts - Retrieve facts about one or more oVirt virtual machines <ovirt_vms_facts_module>

Packet
------

.. toctree:: :maxdepth: 1

  packet_device - create, destroy, start, stop, and reboot a Packet Host machine. <packet_device_module>
  packet_sshkey - Create/delete an SSH key in Packet host. <packet_sshkey_module>

Profitbricks
------------

.. toctree:: :maxdepth: 1

  profitbricks - Create, destroy, start, stop, and reboot a ProfitBricks virtual machine. <profitbricks_module>
  profitbricks_datacenter - Create or destroy a ProfitBricks Virtual Datacenter. <profitbricks_datacenter_module>
  profitbricks_nic - Create or Remove a NIC. <profitbricks_nic_module>
  profitbricks_volume - Create or destroy a volume. <profitbricks_volume_module>
  profitbricks_volume_attachments - Attach or detach a volume. <profitbricks_volume_attachments_module>

Pubnub
------

.. toctree:: :maxdepth: 1

  pubnub_blocks - PubNub blocks management module. <pubnub_blocks_module>

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
  rax_clb_ssl - Manage SSL termination for a Rackspace Cloud Load Balancer. <rax_clb_ssl_module>
  rax_dns - Manage domains on Rackspace Cloud DNS <rax_dns_module>
  rax_dns_record - Manage DNS records on Rackspace Cloud DNS <rax_dns_record_module>
  rax_facts - Gather facts for Rackspace Cloud Servers <rax_facts_module>
  rax_files - Manipulate Rackspace Cloud Files Containers <rax_files_module>
  rax_files_objects - Upload, download, and delete objects in Rackspace Cloud Files <rax_files_objects_module>
  rax_identity - Load Rackspace Cloud Identity <rax_identity_module>
  rax_keypair - Create a keypair for use with Rackspace Cloud Servers <rax_keypair_module>
  rax_meta - Manipulate metadata for Rackspace Cloud Servers <rax_meta_module>
  rax_mon_alarm - Create or delete a Rackspace Cloud Monitoring alarm. <rax_mon_alarm_module>
  rax_mon_check - Create or delete a Rackspace Cloud Monitoring check for an existing entity. <rax_mon_check_module>
  rax_mon_entity - Create or delete a Rackspace Cloud Monitoring entity <rax_mon_entity_module>
  rax_mon_notification - Create or delete a Rackspace Cloud Monitoring notification. <rax_mon_notification_module>
  rax_mon_notification_plan - Create or delete a Rackspace Cloud Monitoring notification plan. <rax_mon_notification_plan_module>
  rax_network - create / delete an isolated network in Rackspace Public Cloud <rax_network_module>
  rax_queue - create / delete a queue in Rackspace Public Cloud <rax_queue_module>
  rax_scaling_group - Manipulate Rackspace Cloud Autoscale Groups <rax_scaling_group_module>
  rax_scaling_policy - Manipulate Rackspace Cloud Autoscale Scaling Policy <rax_scaling_policy_module>

Smartos
-------

.. toctree:: :maxdepth: 1

  imgadm - Manage SmartOS images <imgadm_module>
  smartos_image_facts - Get SmartOS image details. <smartos_image_facts_module>
  vmadm - Manage SmartOS virtual machines and zones. <vmadm_module>

Softlayer
---------

.. toctree:: :maxdepth: 1

  sl_vm - create or cancel a virtual instance in SoftLayer <sl_vm_module>

Univention
----------

.. toctree:: :maxdepth: 1

  udm_dns_record - Manage dns entries on a univention corporate server <udm_dns_record_module>
  udm_dns_zone - Manage dns zones on a univention corporate server <udm_dns_zone_module>
  udm_group - Manage of the posix group <udm_group_module>
  udm_share - Manage samba shares on a univention corporate server <udm_share_module>
  udm_user - Manage posix users on a univention corporate server <udm_user_module>

Vmware
------

.. toctree:: :maxdepth: 1

  vca_fw - add remove firewall rules in a gateway  in a vca <vca_fw_module>
  vca_nat - add remove nat rules in a gateway  in a vca <vca_nat_module>
  vca_vapp - Manages vCloud Air vApp instances. <vca_vapp_module>
  vmware_cluster - Create VMware vSphere Cluster <vmware_cluster_module>
  vmware_datacenter - Manage VMware vSphere Datacenters <vmware_datacenter_module>
  vmware_dns_config - Manage VMware ESXi DNS Configuration <vmware_dns_config_module>
  vmware_dvs_host - Add or remove a host from distributed virtual switch <vmware_dvs_host_module>
  vmware_dvs_portgroup - Create or remove a Distributed vSwitch portgroup <vmware_dvs_portgroup_module>
  vmware_dvswitch - Create or remove a distributed vSwitch <vmware_dvswitch_module>
  vmware_guest - Manages virtual machines in vcenter <vmware_guest_module>
  vmware_guest_facts - Gather facts about a single VM <vmware_guest_facts_module>
  vmware_guest_snapshot - Manages virtual machines snapshots in vcenter <vmware_guest_snapshot_module>
  vmware_host - Add/remove ESXi host to/from vCenter <vmware_host_module>
  vmware_local_user_manager - Manage local users on an ESXi host <vmware_local_user_manager_module>
  vmware_maintenancemode - Place a host into maintenance mode <vmware_maintenancemode_module>
  vmware_migrate_vmk - Migrate a VMK interface from VSS to VDS <vmware_migrate_vmk_module>
  vmware_portgroup - Create a VMware portgroup <vmware_portgroup_module>
  vmware_target_canonical_facts - Return canonical (NAA) from an ESXi host <vmware_target_canonical_facts_module>
  vmware_vm_facts - Return basic facts pertaining to a vSphere virtual machine guest <vmware_vm_facts_module>
  vmware_vm_shell - Execute a process in VM <vmware_vm_shell_module>
  vmware_vm_vss_dvs_migrate - Migrates a virtual machine from a standard vswitch to distributed <vmware_vm_vss_dvs_migrate_module>
  vmware_vmkernel - Create a VMware VMkernel Interface <vmware_vmkernel_module>
  vmware_vmkernel_ip_config - Configure the VMkernel IP Address <vmware_vmkernel_ip_config_module>
  vmware_vmotion - Move a virtual machine using vMotion <vmware_vmotion_module>
  vmware_vsan_cluster - Configure VSAN clustering on an ESXi host <vmware_vsan_cluster_module>
  vmware_vswitch - Add a VMware Standard Switch to an ESXi host <vmware_vswitch_module>
  vsphere_copy - Copy a file to a vCenter datastore <vsphere_copy_module>
  vsphere_guest - Create/delete/manage a guest VM through VMware vSphere. <vsphere_guest_module>

Webfaction
----------

.. toctree:: :maxdepth: 1

  webfaction_app - Add or remove applications on a Webfaction host <webfaction_app_module>
  webfaction_db - Add or remove a database on Webfaction <webfaction_db_module>
  webfaction_domain - Add or remove domains and subdomains on Webfaction <webfaction_domain_module>
  webfaction_mailbox - Add or remove mailboxes on Webfaction <webfaction_mailbox_module>
  webfaction_site - Add or remove a website on a Webfaction host <webfaction_site_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.
       The module documentation details page may explain more about this rationale.
