Network Modules
```````````````

.. toctree:: :maxdepth: 1

  dnsimple (E) - Interface with dnsimple.com (a DNS hosting service). <dnsimple_module>
  dnsmadeeasy (E) - Interface with dnsmadeeasy.com (a DNS hosting service). <dnsmadeeasy_module>
  lldp (E) - get details reported by lldp <lldp_module>
  openvswitch_bridge (E) - Manage Open vSwitch bridges <openvswitch_bridge_module>
  openvswitch_port (E) - Manage Open vSwitch ports <openvswitch_port_module>

A10
---

.. toctree:: :maxdepth: 1

  a10_server (E) - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices <a10_server_module>
  a10_service_group (E) - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices <a10_service_group_module>
  a10_virtual_server (E) - Manage A10 Networks AX/SoftAX/Thunder/vThunder devices <a10_virtual_server_module>

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

F5
--

.. toctree:: :maxdepth: 1

  bigip_facts (E) - Collect facts from F5 BIG-IP devices <bigip_facts_module>
  bigip_monitor_http (E) - Manages F5 BIG-IP LTM http monitors <bigip_monitor_http_module>
  bigip_monitor_tcp (E) - Manages F5 BIG-IP LTM tcp monitors <bigip_monitor_tcp_module>
  bigip_node (E) - Manages F5 BIG-IP LTM nodes <bigip_node_module>
  bigip_pool (E) - Manages F5 BIG-IP LTM pools <bigip_pool_module>
  bigip_pool_member (E) - Manages F5 BIG-IP LTM pool members <bigip_pool_member_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not neccessarily) less activity maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
