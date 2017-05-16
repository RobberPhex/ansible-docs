.. _cs_network:


cs_network - Manages networks on Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update, restart and delete networks.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * cs >= 0.6.10


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
            <tr>
    <td>account<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Account the network is related to.</div></td></tr>
            <tr>
    <td>acl_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>account</td>
        <td><ul><li>account</li><li>domain</li></ul></td>
        <td><div>Access control type.</div><div>Only considered on create.</div></td></tr>
            <tr>
    <td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div></td></tr>
            <tr>
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td><ul></ul></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div></td></tr>
            <tr>
    <td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Secret key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>HTTP timeout.</div></td></tr>
            <tr>
    <td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div></td></tr>
            <tr>
    <td>cidr_ipv6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>CIDR of IPv6 network, must be at least /64.</div><div>Only considered on create.</div></td></tr>
            <tr>
    <td>clean_up<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Cleanup old network elements.</div><div>Only considered on <code>state=restarted</code>.</div></td></tr>
            <tr>
    <td>display_text<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Display text of the network.</div><div>If not specified, <code>name</code> will be used as <code>display_text</code>.</div></td></tr>
            <tr>
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Domain the network is related to.</div></td></tr>
            <tr>
    <td>end_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ending IPv4 address of the network belongs to.</div><div>If not specified, value of <code>start_ip</code> is used.</div><div>Only considered on create.</div></td></tr>
            <tr>
    <td>end_ipv6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ending IPv6 address of the network belongs to.</div><div>If not specified, value of <code>start_ipv6</code> is used.</div><div>Only considered on create.</div></td></tr>
            <tr>
    <td>gateway<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The gateway of the network.</div><div>Required for shared networks and isolated networks when it belongs to a VPC.</div><div>Only considered on create.</div></td></tr>
            <tr>
    <td>gateway_ipv6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The gateway of the IPv6 network.</div><div>Required for shared networks.</div><div>Only considered on create.</div></td></tr>
            <tr>
    <td>isolated_pvlan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The isolated private VLAN for this network.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name (case sensitive) of the network.</div></td></tr>
            <tr>
    <td>netmask<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The netmask of the network.</div><div>Required for shared networks and isolated networks when it belongs to a VPC.</div><div>Only considered on create.</div></td></tr>
            <tr>
    <td>network_domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The network domain.</div></td></tr>
            <tr>
    <td>network_offering<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the offering for the network.</div><div>Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>poll_async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Poll async jobs until job has finished.</div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the project the network to be deployed in.</div></td></tr>
            <tr>
    <td>start_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The beginning IPv4 address of the network belongs to.</div><div>Only considered on create.</div></td></tr>
            <tr>
    <td>start_ipv6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The beginning IPv6 address of the network belongs to.</div><div>Only considered on create.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>restarted</li></ul></td>
        <td><div>State of the network.</div></td></tr>
            <tr>
    <td>vlan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ID or VID of the network.</div></td></tr>
            <tr>
    <td>vpc<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the VPC of the network.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the zone in which the network should be deployed.</div><div>If not set, default zone is used.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # create a network
    - local_action:
        module: cs_network
        name: my network
        zone: gva-01
        network_offering: DefaultIsolatedNetworkOfferingWithSourceNatService
        network_domain: example.com
    
    # update a network
    - local_action:
        module: cs_network
        name: my network
        display_text: network of domain example.local
        network_domain: example.local
    
    # restart a network with clean up
    - local_action:
        module: cs_network
        name: my network
        clean_up: yes
        state: restared
    
    # remove a network
    - local_action:
        module: cs_network
        name: my network
        state: absent

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
        <td> domain </td>
        <td> Domain the network is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ROOT </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> List of resource tags associated with the network. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> [ { "key": "foo", "value": "bar" } ] </td>
    </tr>
            <tr>
        <td> is_persistent </td>
        <td> Whether the network is persistent or not. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> netmask </td>
        <td> IPv4 netmask. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 255.255.255.0 </td>
    </tr>
            <tr>
        <td> network_offering </td>
        <td> The network offering name. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> DefaultIsolatedNetworkOfferingWithSourceNatService </td>
    </tr>
            <tr>
        <td> broadcast_domain_type </td>
        <td> Broadcast domain type of the network. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Vlan </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the network. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 04589590-ac63-4ffc-93f5-b698b8ac38b6 </td>
    </tr>
            <tr>
        <td> gateway_ipv6 </td>
        <td> IPv6 gateway. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2001:db8::1 </td>
    </tr>
            <tr>
        <td> display_text </td>
        <td> Display text of the network. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web project </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the network is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> network_domain </td>
        <td> The network domain </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example.local </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the network. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web project </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> dns2 </td>
        <td> IP address of the 2nd nameserver. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.2.3.4 </td>
    </tr>
            <tr>
        <td> dns1 </td>
        <td> IP address of the 1st nameserver. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.2.3.4 </td>
    </tr>
            <tr>
        <td> cidr_ipv6 </td>
        <td> IPv6 network CIDR. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2001:db8::/64 </td>
    </tr>
            <tr>
        <td> project </td>
        <td> Name of project. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Production </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the network (Allocated, Implemented, Setup). </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Allocated </td>
    </tr>
            <tr>
        <td> gateway </td>
        <td> IPv4 gateway. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.101.64.1 </td>
    </tr>
            <tr>
        <td> cidr </td>
        <td> IPv4 network CIDR. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.101.64.0/24 </td>
    </tr>
            <tr>
        <td> traffic_type </td>
        <td> Traffic type of the network. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Guest </td>
    </tr>
            <tr>
        <td> acl_type </td>
        <td> Access type of the network (Domain, Account). </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Account </td>
    </tr>
            <tr>
        <td> type </td>
        <td> Type of the network. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Isolated </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
.. note:: A detailed guide about cloudstack modules can be found on http://docs.ansible.com/ansible/guide_cloudstack.html
.. note:: This module supports check mode.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

