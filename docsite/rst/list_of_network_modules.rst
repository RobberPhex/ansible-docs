Network Modules
```````````````

.. toctree:: :maxdepth: 1

  cloudflare_dns (E) - manage Cloudflare DNS records <cloudflare_dns_module>
  dnsimple (E) - Interface with dnsimple.com (a DNS hosting service). <dnsimple_module>
  dnsmadeeasy (E) - Interface with dnsmadeeasy.com (a DNS hosting service). <dnsmadeeasy_module>
  haproxy (E) - Enable, disable, and set weights for HAProxy backend servers using socket commands. <haproxy_module>
  ipify_facts (E) - Retrieve the public IP of your internet gateway. <ipify_facts_module>
  lldp (E) - get details reported by lldp <lldp_module>
  nmcli (E) - Manage Networking <nmcli_module>
  openvswitch_bridge (E) - Manage Open vSwitch bridges <openvswitch_bridge_module>
  openvswitch_db (E) - Configure open vswitch database. <openvswitch_db_module>
  openvswitch_port (E) - Manage Open vSwitch ports <openvswitch_port_module>
  snmp_facts (E) - Retrieve facts for a device using SNMP. <snmp_facts_module>
  wakeonlan (E) - Send a magic Wake-on-LAN (WoL) broadcast packet <wakeonlan_module>

A10
---

.. toctree:: :maxdepth: 1

  a10_server (E) - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices <a10_server_module>
  a10_service_group (E) - Manage A10 Networks devices' service groups <a10_service_group_module>
  a10_virtual_server (E) - Manage A10 Networks devices' virtual servers <a10_virtual_server_module>

Asa
---

.. toctree:: :maxdepth: 1

  asa_acl (E) - Manage access-lists on a Cisco ASA <asa_acl_module>
  asa_command (E) - Run arbitrary commands on Cisco ASA devices. <asa_command_module>
  asa_config (E) - Manage Cisco ASA configuration sections <asa_config_module>

Basics
------

.. toctree:: :maxdepth: 1

  get_url - Downloads files from HTTP, HTTPS, or FTP to node <get_url_module>
  slurp - Slurps a file from remote nodes <slurp_module>
  uri - Interacts with webservices <uri_module>

Citrix
------

.. toctree:: :maxdepth: 1

  netscaler (E) - Manages Citrix NetScaler entities <netscaler_module>

Cumulus
-------

.. toctree:: :maxdepth: 1

  cl_bond - Configures a bond port on Cumulus Linux <cl_bond_module>
  cl_bridge - Configures a bridge port on Cumulus Linux <cl_bridge_module>
  cl_img_install - Install a different Cumulus Linux version. <cl_img_install_module>
  cl_interface - Configures a front panel port, loopback or management port on Cumulus Linux. <cl_interface_module>
  cl_interface_policy - Configure interface enforcement policy on Cumulus Linux <cl_interface_policy_module>
  cl_license - Install Cumulus Linux license <cl_license_module>
  cl_ports - Configure Cumulus Switch port attributes (ports.conf) <cl_ports_module>

Dellos10
--------

.. toctree:: :maxdepth: 1

  dellos10_command - Run commands on remote devices running Dell OS10 <dellos10_command_module>
  dellos10_config - Manage Dell OS10 configuration sections <dellos10_config_module>
  dellos10_facts - Collect facts from remote devices running Dell OS10 <dellos10_facts_module>

Dellos6
-------

.. toctree:: :maxdepth: 1

  dellos6_command - Run commands on remote devices running Dell OS6 <dellos6_command_module>
  dellos6_config - Manage Dell OS6 configuration sections <dellos6_config_module>
  dellos6_facts - Collect facts from remote devices running Dell OS6 <dellos6_facts_module>

Dellos9
-------

.. toctree:: :maxdepth: 1

  dellos9_command - Run commands on remote devices running Dell OS9 <dellos9_command_module>
  dellos9_config - Manage Dell OS9 configuration sections <dellos9_config_module>
  dellos9_facts - Collect facts from remote devices running Dell OS9 <dellos9_facts_module>

Eos
---

.. toctree:: :maxdepth: 1

  eos_command - Run arbitrary commands on an Arista EOS device <eos_command_module>
  eos_config - Manage Arista EOS configuration sections <eos_config_module>
  eos_eapi - Manage and configure Arista EOS eAPI. <eos_eapi_module>
  eos_facts - Collect facts from remote devices running Arista EOS <eos_facts_module>
  eos_template (D) - Manage Arista EOS device configurations <eos_template_module>

Exoscale
--------

.. toctree:: :maxdepth: 1

  exo_dns_domain (E) - Manages domain records on Exoscale DNS API. <exo_dns_domain_module>
  exo_dns_record (E) - Manages DNS records on Exoscale DNS. <exo_dns_record_module>

F5
--

.. toctree:: :maxdepth: 1

  bigip_device_dns (E) - Manage BIG-IP device DNS settings <bigip_device_dns_module>
  bigip_device_ntp (E) - Manage NTP servers on a BIG-IP <bigip_device_ntp_module>
  bigip_device_sshd (E) - Manage the SSHD settings of a BIG-IP <bigip_device_sshd_module>
  bigip_facts (E) - Collect facts from F5 BIG-IP devices <bigip_facts_module>
  bigip_gtm_datacenter (E) - Manage Datacenter configuration in BIG-IP <bigip_gtm_datacenter_module>
  bigip_gtm_virtual_server (E) - Manages F5 BIG-IP GTM virtual servers <bigip_gtm_virtual_server_module>
  bigip_gtm_wide_ip (E) - Manages F5 BIG-IP GTM wide ip <bigip_gtm_wide_ip_module>
  bigip_irule (E) - Manage iRules across different modules on a BIG-IP. <bigip_irule_module>
  bigip_monitor_http (E) - Manages F5 BIG-IP LTM http monitors <bigip_monitor_http_module>
  bigip_monitor_tcp (E) - Manages F5 BIG-IP LTM tcp monitors <bigip_monitor_tcp_module>
  bigip_node (E) - Manages F5 BIG-IP LTM nodes <bigip_node_module>
  bigip_pool (E) - Manages F5 BIG-IP LTM pools <bigip_pool_module>
  bigip_pool_member (E) - Manages F5 BIG-IP LTM pool members <bigip_pool_member_module>
  bigip_routedomain (E) - Manage route domains on a BIG-IP <bigip_routedomain_module>
  bigip_selfip (E) - Manage Self-IPs on a BIG-IP system <bigip_selfip_module>
  bigip_ssl_certificate (E) - Import/Delete certificates from BIG-IP <bigip_ssl_certificate_module>
  bigip_sys_db (E) - Manage BIG-IP system database variables <bigip_sys_db_module>
  bigip_virtual_server (E) - Manages F5 BIG-IP LTM virtual servers <bigip_virtual_server_module>
  bigip_vlan (E) - Manage VLANs on a BIG-IP system <bigip_vlan_module>

Illumos
-------

.. toctree:: :maxdepth: 1

  dladm_etherstub (E) - Manage etherstubs on Solaris/illumos systems. <dladm_etherstub_module>
  dladm_vnic (E) - Manage VNICs on Solaris/illumos systems. <dladm_vnic_module>
  flowadm (E) - Manage bandwidth resource control and priority for protocols, services and zones. <flowadm_module>
  ipadm_if (E) - Manage IP interfaces  on Solaris/illumos systems. <ipadm_if_module>
  ipadm_prop (E) - Manage protocol properties on Solaris/illumos systems. <ipadm_prop_module>

Ios
---

.. toctree:: :maxdepth: 1

  ios_command - Run commands on remote devices running Cisco IOS <ios_command_module>
  ios_config - Manage Cisco IOS configuration sections <ios_config_module>
  ios_facts - Collect facts from remote devices running IOS <ios_facts_module>
  ios_template (D) - Manage Cisco IOS device configurations over SSH <ios_template_module>

Iosxr
-----

.. toctree:: :maxdepth: 1

  iosxr_command - Run commands on remote devices running Cisco iosxr <iosxr_command_module>
  iosxr_config - Manage Cisco IOS XR configuration sections <iosxr_config_module>
  iosxr_facts - Collect facts from remote devices running IOS-XR <iosxr_facts_module>
  iosxr_template (D) - Manage Cisco IOSXR device configurations over SSH <iosxr_template_module>

Junos
-----

.. toctree:: :maxdepth: 1

  junos_command - Execute arbitrary commands on a remote device running Junos <junos_command_module>
  junos_config - Manage configuration on devices running Juniper JUNOS <junos_config_module>
  junos_facts - Collect facts from remote device running Junos <junos_facts_module>
  junos_netconf - Configures the Junos Netconf system service <junos_netconf_module>
  junos_package - Installs packages on remote devices running Junos <junos_package_module>
  junos_template (D) - Manage configuration on remote devices running Junos <junos_template_module>

Netconf
-------

.. toctree:: :maxdepth: 1

  netconf_config (E) - netconf device configuration <netconf_config_module>

Netvisor
--------

.. toctree:: :maxdepth: 1

  pn_cluster - CLI command to create/delete a cluster. <pn_cluster_module>
  pn_ospf - CLI command to add/remove ospf protocol to a vRouter. <pn_ospf_module>
  pn_ospfarea - CLI command to add/remove ospf area to/from a vrouter. <pn_ospfarea_module>
  pn_show - Run show commands on nvOS device. <pn_show_module>
  pn_trunk - CLI command to create/delete/modify a trunk. <pn_trunk_module>
  pn_vlag - CLI command to create/delete/modify vlag. <pn_vlag_module>
  pn_vlan - CLI command to create/delete a VLAN. <pn_vlan_module>
  pn_vrouter - CLI command to create/delete/modify a vrouter. <pn_vrouter_module>
  pn_vrouterbgp - CLI command to add/remove/modify vrouter-bgp. <pn_vrouterbgp_module>
  pn_vrouterif - CLI command to add/remove/modify vrouter-interface. <pn_vrouterif_module>
  pn_vrouterlbif - CLI command to add/remove vrouter-loopback-interface. <pn_vrouterlbif_module>

Nxos
----

.. toctree:: :maxdepth: 1

  nxos_aaa_server - Manages AAA server global configuration. <nxos_aaa_server_module>
  nxos_aaa_server_host - Manages AAA server host-specific configuration. <nxos_aaa_server_host_module>
  nxos_acl - Manages access list entries for ACLs. <nxos_acl_module>
  nxos_acl_interface - Manages applying ACLs to interfaces. <nxos_acl_interface_module>
  nxos_bgp - Manages BGP configuration. <nxos_bgp_module>
  nxos_bgp_af - Manages BGP Address-family configuration. <nxos_bgp_af_module>
  nxos_bgp_neighbor - Manages BGP neighbors configurations. <nxos_bgp_neighbor_module>
  nxos_bgp_neighbor_af - Manages BGP address-family's neighbors configuration. <nxos_bgp_neighbor_af_module>
  nxos_command - Run arbitrary command on Cisco NXOS devices <nxos_command_module>
  nxos_config - Manage Cisco NXOS configuration sections <nxos_config_module>
  nxos_evpn_global - Handles the EVPN control plane for VXLAN. <nxos_evpn_global_module>
  nxos_evpn_vni - Manages Cisco EVPN VXLAN Network Identifier (VNI). <nxos_evpn_vni_module>
  nxos_facts - Gets facts about NX-OS switches <nxos_facts_module>
  nxos_feature - Manage features in NX-OS switches. <nxos_feature_module>
  nxos_file_copy - Copy a file to a remote NXOS device over SCP. <nxos_file_copy_module>
  nxos_gir - Trigger a graceful removal or insertion (GIR) of the switch. <nxos_gir_module>
  nxos_gir_profile_management - Create a maintenance-mode or normal-mode profile for GIR. <nxos_gir_profile_management_module>
  nxos_hsrp - Manages HSRP configuration on NX-OS switches. <nxos_hsrp_module>
  nxos_igmp - Manages IGMP global configuration. <nxos_igmp_module>
  nxos_igmp_interface - Manages IGMP interface configuration. <nxos_igmp_interface_module>
  nxos_igmp_snooping - Manages IGMP snooping global configuration. <nxos_igmp_snooping_module>
  nxos_install_os - Set boot options like boot image and kickstart image. <nxos_install_os_module>
  nxos_interface - Manages physical attributes of interfaces. <nxos_interface_module>
  nxos_interface_ospf - Manages configuration of an OSPF interface instance. <nxos_interface_ospf_module>
  nxos_ip_interface - Manages L3 attributes for IPv4 and IPv6 interfaces. <nxos_ip_interface_module>
  nxos_mtu - Manages MTU settings on Nexus switch. <nxos_mtu_module>
  nxos_ntp - Manages core NTP configuration. <nxos_ntp_module>
  nxos_ntp_auth - Manages NTP authentication. <nxos_ntp_auth_module>
  nxos_ntp_options - Manages NTP options. <nxos_ntp_options_module>
  nxos_nxapi - Manage NXAPI configuration on an NXOS device. <nxos_nxapi_module>
  nxos_ospf - Manages configuration of an ospf instance. <nxos_ospf_module>
  nxos_ospf_vrf - Manages a VRF for an OSPF router. <nxos_ospf_vrf_module>
  nxos_overlay_global - Configures anycast gateway MAC of the switch. <nxos_overlay_global_module>
  nxos_pim - Manages configuration of a PIM instance. <nxos_pim_module>
  nxos_pim_interface - Manages PIM interface configuration. <nxos_pim_interface_module>
  nxos_pim_rp_address - Manages configuration of an PIM static RP address instance. <nxos_pim_rp_address_module>
  nxos_ping - Tests reachability using ping from Nexus switch. <nxos_ping_module>
  nxos_portchannel - Manages port-channel interfaces. <nxos_portchannel_module>
  nxos_reboot - Reboot a network device. <nxos_reboot_module>
  nxos_rollback - Set a checkpoint or rollback to a checkpoint. <nxos_rollback_module>
  nxos_smu - Perform SMUs on Cisco NX-OS devices. <nxos_smu_module>
  nxos_snapshot - Manage snapshots of the running states of selected features. <nxos_snapshot_module>
  nxos_snmp_community - Manages SNMP community configs. <nxos_snmp_community_module>
  nxos_snmp_contact - Manages SNMP contact info. <nxos_snmp_contact_module>
  nxos_snmp_host - Manages SNMP host configuration. <nxos_snmp_host_module>
  nxos_snmp_location - Manages SNMP location information. <nxos_snmp_location_module>
  nxos_snmp_traps - Manages SNMP traps. <nxos_snmp_traps_module>
  nxos_snmp_user - Manages SNMP users for monitoring. <nxos_snmp_user_module>
  nxos_static_route - Manages static route configuration <nxos_static_route_module>
  nxos_switchport - Manages Layer 2 switchport interfaces. <nxos_switchport_module>
  nxos_template (D) - Manage Cisco NXOS device configurations <nxos_template_module>
  nxos_udld - Manages UDLD global configuration params. <nxos_udld_module>
  nxos_udld_interface - Manages UDLD interface configuration params. <nxos_udld_interface_module>
  nxos_vlan - Manages VLAN resources and attributes. <nxos_vlan_module>
  nxos_vpc - Manages global VPC configuration <nxos_vpc_module>
  nxos_vpc_interface - Manages interface VPC configuration <nxos_vpc_interface_module>
  nxos_vrf - Manages global VRF configuration. <nxos_vrf_module>
  nxos_vrf_af - Manages VRF AF. <nxos_vrf_af_module>
  nxos_vrf_interface - Manages interface specific VRF configuration. <nxos_vrf_interface_module>
  nxos_vrrp - Manages VRRP configuration on NX-OS switches. <nxos_vrrp_module>
  nxos_vtp_domain - Manages VTP domain configuration. <nxos_vtp_domain_module>
  nxos_vtp_password - Manages VTP password configuration. <nxos_vtp_password_module>
  nxos_vtp_version - Manages VTP version configuration. <nxos_vtp_version_module>
  nxos_vxlan_vtep - Manages VXLAN Network Virtualization Endpoint (NVE). <nxos_vxlan_vtep_module>
  nxos_vxlan_vtep_vni - Creates a Virtual Network Identifier member (VNI) <nxos_vxlan_vtep_vni_module>

Openswitch
----------

.. toctree:: :maxdepth: 1

  ops_command - Run arbitrary commands on OpenSwitch devices. <ops_command_module>
  ops_config - Manage OpenSwitch configuration using CLI <ops_config_module>
  ops_facts - Collect device specific facts from OpenSwitch <ops_facts_module>
  ops_template (D) - Push configuration to OpenSwitch <ops_template_module>

Sros
----

.. toctree:: :maxdepth: 1

  sros_command - Run commands on remote devices running Nokia SR OS <sros_command_module>
  sros_config - Manage Nokia SR OS device configuration <sros_config_module>
  sros_rollback - Configure Nokia SR OS rollback <sros_rollback_module>

Vyos
----

.. toctree:: :maxdepth: 1

  vyos_command - Run one or more commands on VyOS devices <vyos_command_module>
  vyos_config - Manage VyOS configuration on remote device <vyos_config_module>
  vyos_facts - Collect facts from remote devices running OS <vyos_facts_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
