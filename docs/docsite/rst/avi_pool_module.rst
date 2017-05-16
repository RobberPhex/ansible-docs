.. _avi_pool:


avi_pool - Module for setup of Pool Avi RESTful Object
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module is used to configure Pool object
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
                <tr><td>a_pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of container cloud application that constitutes a pool in a a-b pool configuration, if different from vs app.</div>        </td></tr>
                <tr><td>ab_pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A/b pool configuration.</div>        </td></tr>
                <tr><td>ab_priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Priority of this pool in a a-b pool pair.</div><div>Internally used.</div>        </td></tr>
                <tr><td>apic_epg_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Synchronize cisco apic epg members with pool servers.</div>        </td></tr>
                <tr><td>application_persistence_profile_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Persistence will ensure the same user sticks to the same server for a desired duration of time.</div><div>It is a reference to an object of type applicationpersistenceprofile.</div>        </td></tr>
                <tr><td>autoscale_launch_config_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Reference to the launch configuration profile.</div><div>It is a reference to an object of type autoscalelaunchconfig.</div>        </td></tr>
                <tr><td>autoscale_networks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Network ids for the launch configuration.</div>        </td></tr>
                <tr><td>autoscale_policy_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Reference to server autoscale policy.</div><div>It is a reference to an object of type serverautoscalepolicy.</div>        </td></tr>
                <tr><td>capacity_estimation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Inline estimation of capacity of servers.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>capacity_estimation_ttfb_thresh<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The maximum time-to-first-byte of a server.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 0.</div>        </td></tr>
                <tr><td>cloud_config_cksum<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Checksum of cloud configuration for pool.</div><div>Internally set by cloud connector.</div>        </td></tr>
                <tr><td>cloud_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>It is a reference to an object of type cloud.</div>        </td></tr>
                <tr><td>connection_ramp_duration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Duration for which new connections will be gradually ramped up to a server recently brought online.</div><div>Useful for lb algorithms that are least connection based.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 10.</div>        </td></tr>
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
                <tr><td>default_server_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Traffic sent to servers will use this destination server port unless overridden by the server's specific port attribute.</div><div>The ssl checkbox enables avi to server encryption.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 80.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A description of the pool.</div>        </td></tr>
                <tr><td>domain_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Comma separated list of domain names which will be used to verify the common names or subject alternative names presented by server certificates.</div><div>It is performed only when common name check host_check_enabled is enabled.</div>        </td></tr>
                <tr><td>east_west<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Inherited config from virtualservice.</div>        </td></tr>
                <tr><td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable or disable the pool.</div><div>Disabling will terminate all open connections and pause health monitors.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as True.</div>        </td></tr>
                <tr><td>fail_action<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable an action - close connection, http redirect, local http response, or backup pool - when a pool failure happens.</div><div>By default, a connection will be closed, in case the pool experiences a failure.</div>        </td></tr>
                <tr><td>fewest_tasks_feedback_delay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Periodicity of feedback for fewest tasks server selection algorithm.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 10.</div>        </td></tr>
                <tr><td>graceful_disable_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Used to gracefully disable a server.</div><div>Virtual service waits for the specified time before terminating the existing connections  to the servers that are disabled.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 1.</div>        </td></tr>
                <tr><td>health_monitor_refs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Verify server health by applying one or more health monitors.</div><div>Active monitors generate synthetic traffic from each service engine and mark a server up or down based on the response.</div><div>The passive monitor listens only to client to server communication.</div><div>It raises or lowers the ratio of traffic destined to a server based on successful responses.</div><div>It is a reference to an object of type healthmonitor.</div>        </td></tr>
                <tr><td>host_check_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable common name check for server certificate.</div><div>If enabled and no explicit domain name is specified, avi will use the incoming host header to do the match.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>inline_health_monitor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The passive monitor will monitor client to server connections and requests and adjust traffic load to servers based on successful responses.</div><div>This may alter the expected behavior of the lb method, such as round robin.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as True.</div>        </td></tr>
                <tr><td>ipaddrgroup_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Use list of servers from ip address group.</div><div>It is a reference to an object of type ipaddrgroup.</div>        </td></tr>
                <tr><td>lb_algorithm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The load balancing algorithm will pick a server within the pool's list of available servers.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as LB_ALGORITHM_LEAST_CONNECTIONS.</div>        </td></tr>
                <tr><td>lb_algorithm_consistent_hash_hdr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Http header name to be used for the hash key.</div>        </td></tr>
                <tr><td>lb_algorithm_hash<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Criteria used as a key for determining the hash between the client and  server.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as LB_ALGORITHM_CONSISTENT_HASH_SOURCE_IP_ADDRESS.</div>        </td></tr>
                <tr><td>max_concurrent_connections_per_server<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The maximum number of concurrent connections allowed to each server within the pool.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 0.</div>        </td></tr>
                <tr><td>max_conn_rate_per_server<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rate limit connections to each server.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the pool.</div>        </td></tr>
                <tr><td>networks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>(internal-use) networks designated as containing servers for this pool.</div><div>The servers may be further narrowed down by a filter.</div><div>This field is used internally by avi, not editable by the user.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of Avi user in Avi controller. The default value is the environment variable <code>AVI_PASSWORD</code>.</div>        </td></tr>
                <tr><td>pki_profile_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Avi will validate the ssl certificate present by a server against the selected pki profile.</div><div>It is a reference to an object of type pkiprofile.</div>        </td></tr>
                <tr><td>placement_networks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Manually select the networks and subnets used to provide reachability to the pool's servers.</div><div>Specify the subnet using the following syntax  10-1-1-0/24.</div><div>Use static routes in vrf configuration when pool servers are not directly connected butroutable from the service engine.</div>        </td></tr>
                <tr><td>prst_hdr_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Header name for custom header persistence.</div>        </td></tr>
                <tr><td>request_queue_depth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Minimum number of requests to be queued when pool is full.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 128.</div>        </td></tr>
                <tr><td>request_queue_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable request queue when pool is full.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>rewrite_host_header_to_server_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rewrite incoming host header to server name of the server to which the request is proxied.</div><div>Enabling this feature rewrites host header for requests to all servers in the pool.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>rewrite_host_header_to_sni<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If sni server name is specified, rewrite incoming host header to the sni server name.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>server_auto_scale<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Server autoscale.</div><div>Not used anymore.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>server_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of server_count.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 0.</div>        </td></tr>
                <tr><td>server_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Fully qualified dns hostname which will be used in the tls sni extension in server connections if sni is enabled.</div><div>If no value is specified, avi will use the incoming host header instead.</div>        </td></tr>
                <tr><td>server_reselect<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Server reselect configuration for http requests.</div>        </td></tr>
                <tr><td>servers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The pool directs load balanced traffic to this list of destination servers.</div><div>The servers can be configured by ip address, name, network or via ip address group.</div>        </td></tr>
                <tr><td>sni_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable tls sni for server connections.</div><div>If disabled, avi will not send the sni extension as part of the handshake.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as True.</div>        </td></tr>
                <tr><td>ssl_key_and_certificate_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Service engines will present a client ssl certificate to the server.</div><div>It is a reference to an object of type sslkeyandcertificate.</div>        </td></tr>
                <tr><td>ssl_profile_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When enabled, avi re-encrypts traffic to the backend servers.</div><div>The specific ssl profile defines which ciphers and ssl versions will be supported.</div><div>It is a reference to an object of type sslprofile.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>The state that should be applied on the entity.</div>        </td></tr>
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
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Avi controller URL of the object.</div>        </td></tr>
                <tr><td>use_service_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Do not translate the client's destination port when sending the connection to the server.</div><div>The pool or servers specified service port will still be used for health monitoring.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username used for accessing Avi controller. The default value is the environment variable <code>AVI_USERNAME</code>.</div>        </td></tr>
                <tr><td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uuid of the pool.</div>        </td></tr>
                <tr><td>vrf_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Virtual routing context that the pool is bound to.</div><div>This is used to provide the isolation of the set of networks the pool is attached to.</div><div>The pool inherits the virtual routing conext of the virtual service, and this field is used only internally, and is set by pb-transform.</div><div>It is a reference to an object of type vrfcontext.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a Pool with two servers and HTTP monitor
      avi_pool:
        controller: 10.10.1.20
        username: avi_user
        password: avi_password
        name: testpool1
        description: testpool1
        state: present
        health_monitor_refs:
            - '/api/healthmonitor?name=System-HTTP'
        servers:
            - ip:
                addr: 10.10.2.20
                type: V4
            - ip:
                addr: 10.10.2.21
                type: V4

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
        <td> Pool (api/pool) object </td>
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
