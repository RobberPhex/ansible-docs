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

A10
---

.. toctree:: :maxdepth: 1

  a10_server (E) - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices <a10_server_module>
  a10_service_group (E) - Manage A10 Networks devices' service groups <a10_service_group_module>
  a10_virtual_server (E) - Manage A10 Networks devices' virtual servers <a10_virtual_server_module>

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

Eos
---

.. toctree:: :maxdepth: 1

  eos_command - Run arbitrary command on EOS device <eos_command_module>
  eos_config - Manage Arista EOS configuration sections <eos_config_module>
  eos_eapi - Manage and configure EAPI. Requires EOS v4.12 or greater. <eos_eapi_module>
  eos_template - Manage Arista EOS device configurations <eos_template_module>

F5
--

.. toctree:: :maxdepth: 1

  bigip_facts (E) - Collect facts from F5 BIG-IP devices <bigip_facts_module>
  bigip_gtm_wide_ip (E) - Manages F5 BIG-IP GTM wide ip <bigip_gtm_wide_ip_module>
  bigip_monitor_http (E) - Manages F5 BIG-IP LTM http monitors <bigip_monitor_http_module>
  bigip_monitor_tcp (E) - Manages F5 BIG-IP LTM tcp monitors <bigip_monitor_tcp_module>
  bigip_node (E) - Manages F5 BIG-IP LTM nodes <bigip_node_module>
  bigip_pool (E) - Manages F5 BIG-IP LTM pools <bigip_pool_module>
  bigip_pool_member (E) - Manages F5 BIG-IP LTM pool members <bigip_pool_member_module>
  bigip_virtual_server (E) - Manages F5 BIG-IP LTM virtual servers <bigip_virtual_server_module>

Ios
---

.. toctree:: :maxdepth: 1

  ios_command - Run arbitrary commands on ios devices. <ios_command_module>
  ios_config - Manage Cisco IOS configuration sections <ios_config_module>
  ios_template - Manage Cisco IOS device configurations over SSH <ios_template_module>

Iosxr
-----

.. toctree:: :maxdepth: 1

  iosxr_command - Run arbitrary commands on ios devices. <iosxr_command_module>
  iosxr_config - Manage Cisco IOS XR configuration sections <iosxr_config_module>
  iosxr_template - Manage Cisco IOSXR device configurations over SSH <iosxr_template_module>

Junos
-----

.. toctree:: :maxdepth: 1

  junos_command - Execute arbitrary commands on a remote device running Junos <junos_command_module>
  junos_config - Manage configuration on remote devices running Junos <junos_config_module>
  junos_facts - Collect facts from remove device running Junos <junos_facts_module>
  junos_netconf - Configures the Junos Netconf system service <junos_netconf_module>
  junos_package - Installs packages on remote devices running Junos <junos_package_module>
  junos_template - Manage configuration on remote devices running Junos <junos_template_module>

Nxos
----

.. toctree:: :maxdepth: 1

  nxos_command - Run arbitrary command on Cisco NXOS devices <nxos_command_module>
  nxos_config - Manage Cisco NXOS configuration sections <nxos_config_module>
  nxos_facts - Gets facts about NX-OS switches <nxos_facts_module>
  nxos_feature - Manage features in NX-OS switches <nxos_feature_module>
  nxos_interface - Manages physical attributes of interfaces <nxos_interface_module>
  nxos_ip_interface - Manages L3 attributes for IPv4 and IPv6 interfaces <nxos_ip_interface_module>
  nxos_nxapi - Manage NXAPI configuration on an NXOS device. <nxos_nxapi_module>
  nxos_ping - Tests reachability using ping from Nexus switch <nxos_ping_module>
  nxos_switchport - Manages Layer 2 switchport interfaces <nxos_switchport_module>
  nxos_template - Manage Cisco NXOS device configurations <nxos_template_module>
  nxos_vlan - Manages VLAN resources and attributes <nxos_vlan_module>
  nxos_vrf - Manages global VRF configuration <nxos_vrf_module>
  nxos_vrf_interface - Manages interface specific VRF configuration <nxos_vrf_interface_module>
  nxos_vrrp - Manages VRRP configuration on NX-OS switches <nxos_vrrp_module>

Openswitch
----------

.. toctree:: :maxdepth: 1

  ops_command - Run arbitrary commands on OpenSwitch devices. <ops_command_module>
  ops_config - Manage OpenSwitch configuration using CLI <ops_config_module>
  ops_facts - Collect device specific facts from OpenSwitch <ops_facts_module>
  ops_template - Push configuration to OpenSwitch <ops_template_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
