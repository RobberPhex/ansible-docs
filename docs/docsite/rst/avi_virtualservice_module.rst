.. _avi_virtualservice:


avi_virtualservice - Module for setup of VirtualService Avi RESTful Object
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module is used to configure VirtualService object
* more examples at https://github.com/avinetworks/devops


Requirements (on host that executes module)
-------------------------------------------

  * avisdk


Options
-------

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                <tr><td>active_standby_se_tag<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This configuration only applies if the virtualservice is in legacy active standby ha mode and load distribution among active standby is enabled.</div><div>This field is used to tag the virtualservice so that virtualservices with the same tag will share the same active serviceengine.</div><div>Virtualservices with different tags will have different active serviceengines.</div><div>If one of the serviceengine's in the serviceenginegroup fails, all virtualservices will end up using the same active serviceengine.</div><div>Redistribution of the virtualservices can be either manual or automated when the failed serviceengine recovers.</div><div>Redistribution is based on the auto redistribute property of the serviceenginegroup.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as ACTIVE_STANDBY_SE_1.</div>        </td></tr>
                <tr><td>analytics_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Determines analytics settings for the application.</div>        </td></tr>
                <tr><td>analytics_profile_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies settings related to analytics.</div><div>It is a reference to an object of type analyticsprofile.</div>        </td></tr>
                <tr><td>application_profile_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable application layer specific features for the virtual service.</div><div>It is a reference to an object of type applicationprofile.</div>        </td></tr>
                <tr><td>auto_allocate_floating_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Auto-allocate floating/elastic ip from the cloud infrastructure.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>auto_allocate_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Auto-allocate vip from the provided subnet.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>availability_zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Availability-zone to place the virtual service.</div>        </td></tr>
                <tr><td>avi_allocated_fip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>(internal-use) fip allocated by avi in the cloud infrastructure.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>avi_allocated_vip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>(internal-use) vip allocated by avi in the cloud infrastructure.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>client_auth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Http authentication configuration for protected resources.</div>        </td></tr>
                <tr><td>cloud_config_cksum<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Checksum of cloud configuration for vs.</div><div>Internally set by cloud connector.</div>        </td></tr>
                <tr><td>cloud_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>It is a reference to an object of type cloud.</div>        </td></tr>
                <tr><td>cloud_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Cloud_type of virtualservice.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as CLOUD_NONE.</div>        </td></tr>
                <tr><td>connections_rate_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rate limit the incoming connections to this virtual service.</div>        </td></tr>
                <tr><td>content_rewrite<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Profile used to match and rewrite strings in request and/or response body.</div>        </td></tr>
                <tr><td>controller<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IP address or hostname of the controller. The default value is the environment variable <code>AVI_CONTROLLER</code>.</div>        </td></tr>
                <tr><td>created_by<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Creator name.</div>        </td></tr>
                <tr><td>delay_fairness<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Select the algorithm for qos fairness.</div><div>This determines how multiple virtual services sharing the same service engines will prioritize traffic over a congested network.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>User defined description for the object.</div>        </td></tr>
                <tr><td>discovered_network_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>(internal-use) discovered networks providing reachability for client facing virtual service ip.</div><div>This field is deprecated.</div><div>It is a reference to an object of type network.</div>        </td></tr>
                <tr><td>discovered_networks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>(internal-use) discovered networks providing reachability for client facing virtual service ip.</div><div>This field is used internally by avi, not editable by the user.</div>        </td></tr>
                <tr><td>discovered_subnet<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>(internal-use) discovered subnets providing reachability for client facing virtual service ip.</div><div>This field is deprecated.</div>        </td></tr>
                <tr><td>dns_info<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Service discovery specific data including fully qualified domain name, type and time-to-live of the dns record.</div><div>Note that only one of fqdn and dns_info setting is allowed.</div>        </td></tr>
                <tr><td>east_west_placement<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Force placement on all se's in service group (mesos mode only).</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>enable_autogw<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Response traffic to clients will be sent back to the source mac address of the connection, rather than statically sent to a default gateway.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as True.</div>        </td></tr>
                <tr><td>enable_rhi<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable route health injection using the bgp config in the vrf context.</div>        </td></tr>
                <tr><td>enable_rhi_snat<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable route health injection for source nat'ted floating ip address using the bgp config in the vrf context.</div>        </td></tr>
                <tr><td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable or disable the virtual service.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as True.</div>        </td></tr>
                <tr><td>floating_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Floating ip to associate with this virtual service.</div>        </td></tr>
                <tr><td>floating_subnet_uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If auto_allocate_floating_ip is true and more than one floating-ip subnets exist, then the subnet for the floating ip address allocation.</div><div>This field is applicable only if the virtualservice belongs to an openstack or aws cloud.</div><div>In openstack or aws cloud it is required when auto_allocate_floating_ip is selected.</div>        </td></tr>
                <tr><td>flow_dist<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Criteria for flow distribution among ses.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as LOAD_AWARE.</div>        </td></tr>
                <tr><td>flow_label_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Criteria for flow labelling.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as NO_LABEL.</div>        </td></tr>
                <tr><td>fqdn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dns resolvable, fully qualified domain name of the virtualservice.</div><div>Only one of 'fqdn' and 'dns_info' configuration is allowed.</div>        </td></tr>
                <tr><td>host_name_xlate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Translate the host name sent to the servers to this value.</div><div>Translate the host name sent from servers back to the value used by the client.</div>        </td></tr>
                <tr><td>http_policies<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Http policies applied on the data traffic of the virtual service.</div>        </td></tr>
                <tr><td>ign_pool_net_reach<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ignore pool servers network reachability constraints for virtual service placement.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ip address of the virtual service.</div>        </td></tr>
                <tr><td>ipam_network_subnet<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Subnet and/or network for allocating virtualservice ip by ipam provider module.</div>        </td></tr>
                <tr><td>limit_doser<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Limit potential dos attackers who exceed max_cps_per_client significantly to a fraction of max_cps_per_client for a while.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>max_cps_per_client<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum connections per second per client ip.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 0.</div>        </td></tr>
                <tr><td>microservice_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Microservice representing the virtual service.</div><div>It is a reference to an object of type microservice.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name for the virtual service.</div>        </td></tr>
                <tr><td>network_profile_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Determines network settings such as protocol, tcp or udp, and related options for the protocol.</div><div>It is a reference to an object of type networkprofile.</div>        </td></tr>
                <tr><td>network_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Manually override the network on which the virtual service is placed.</div><div>It is a reference to an object of type network.</div>        </td></tr>
                <tr><td>network_security_policy_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Network security policies for the virtual service.</div><div>It is a reference to an object of type networksecuritypolicy.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of Avi user in Avi controller. The default value is the environment variable <code>AVI_PASSWORD</code>.</div>        </td></tr>
                <tr><td>performance_limits<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Optional settings that determine performance limits like max connections or bandwdith etc.</div>        </td></tr>
                <tr><td>pool_group_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The pool group is an object that contains pools.</div><div>It is a reference to an object of type poolgroup.</div>        </td></tr>
                <tr><td>pool_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The pool is an object that contains destination servers and related attributes such as load-balancing and persistence.</div><div>It is a reference to an object of type pool.</div>        </td></tr>
                <tr><td>port_uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>(internal-use) network port assigned to the virtual service ip address.</div>        </td></tr>
                <tr><td>remove_listening_port_on_vs_down<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Remove listening port if virtualservice is down.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>requests_rate_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rate limit the incoming requests to this virtual service.</div>        </td></tr>
                <tr><td>scaleout_ecmp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Disable re-distribution of flows across service engines for a virtual service.</div><div>Enable if the network itself performs flow hashing with ecmp in environments such as gcp.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>se_group_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The service engine group to use for this virtual service.</div><div>Moving to a new se group is disruptive to existing connections for this vs.</div><div>It is a reference to an object of type serviceenginegroup.</div>        </td></tr>
                <tr><td>server_network_profile_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Determines the network settings profile for the server side of tcp proxied connections.</div><div>Leave blank to use the same settings as the client to vs side of the connection.</div><div>It is a reference to an object of type networkprofile.</div>        </td></tr>
                <tr><td>service_pool_select<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Select pool based on destination port.</div>        </td></tr>
                <tr><td>services<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of services defined for this virtual service.</div>        </td></tr>
                <tr><td>snat_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Nat'ted floating source ip address(es) for upstream connection to servers.</div>        </td></tr>
                <tr><td>ssl_key_and_certificate_refs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Select or create one or two certificates, ec and/or rsa, that will be presented to ssl/tls terminated connections.</div><div>It is a reference to an object of type sslkeyandcertificate.</div>        </td></tr>
                <tr><td>ssl_profile_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Determines the set of ssl versions and ciphers to accept for ssl/tls terminated connections.</div><div>It is a reference to an object of type sslprofile.</div>        </td></tr>
                <tr><td>ssl_sess_cache_avg_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Expected number of ssl session cache entries (may be exceeded).</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 1024.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>The state that should be applied on the entity.</div>        </td></tr>
                <tr><td>static_dns_records<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of static dns records applied to this virtual service.</div><div>These are static entries and no health monitoring is performed against the ip addresses.</div>        </td></tr>
                <tr><td>subnet<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Subnet providing reachability for client facing virtual service ip.</div>        </td></tr>
                <tr><td>subnet_uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>It represents subnet for the virtual service ip address allocation when auto_allocate_ip is true.it is only applicable in openstack or aws cloud.</div><div>This field is required if auto_allocate_ip is true.</div>        </td></tr>
                <tr><td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>Name of tenant used for all Avi API calls and context of object.</div>        </td></tr>
                <tr><td>tenant_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>It is a reference to an object of type tenant.</div>        </td></tr>
                <tr><td>tenant_uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>UUID of tenant used for all Avi API calls and context of object.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if this is a normal virtual service, or if it is the parent or child of an sni-enabled virtual hosted virtual service.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as VS_TYPE_NORMAL.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Avi controller URL of the object.</div>        </td></tr>
                <tr><td>use_bridge_ip_as_vip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Use bridge ip as vip on each host in mesos deployments.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username used for accessing Avi controller. The default value is the environment variable <code>AVI_USERNAME</code>.</div>        </td></tr>
                <tr><td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uuid of the virtualservice.</div>        </td></tr>
                <tr><td>vh_domain_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The exact name requested from the client's sni-enabled tls hello domain name field.</div><div>If this is a match, the parent vs will forward the connection to this child vs.</div>        </td></tr>
                <tr><td>vh_parent_vs_uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the virtual service acting as virtual hosting (sni) parent.</div>        </td></tr>
                <tr><td>vrf_context_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Virtual routing context that the virtual service is bound to.</div><div>This is used to provide the isolation of the set of networks the application is attached to.</div><div>It is a reference to an object of type vrfcontext.</div>        </td></tr>
                <tr><td>vs_datascripts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Datascripts applied on the data traffic of the virtual service.</div>        </td></tr>
                <tr><td>weight<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The quality of service weight to assign to traffic transmitted from this virtual service.</div><div>A higher weight will prioritize traffic versus other virtual services sharing the same service engines.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 1.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create SSL Virtual Service using Pool testpool2
      avi_virtualservice:
        controller: 10.10.27.90
        username: admin
        password: AviNetworks123!
        name: newtestvs
        state: present
        performance_limits:
        max_concurrent_connections: 1000
        services:
            - port: 443
              enable_ssl: true
            - port: 80
        ssl_profile_ref: '/api/sslprofile?name=System-Standard'
        application_profile_ref: '/api/applicationprofile?name=System-Secure-HTTP'
        ssl_key_and_certificate_refs:
            - '/api/sslkeyandcertificate?name=System-Default-Cert'
        ip_address:
        addr: 10.90.131.103
        type: V4
        pool_ref: '/api/pool?name=testpool2'

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> obj </td>
        <td> VirtualService (api/virtualservice) object </td>
        <td align=center> success, changed </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
