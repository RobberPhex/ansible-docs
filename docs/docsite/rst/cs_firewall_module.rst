.. _cs_firewall:


cs_firewall - Manages firewall rules on Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates and removes firewall rules.


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
                <tr><td>account<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Account the firewall rule is related to.</div>        </td></tr>
                <tr><td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div>        </td></tr>
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>API key of the CloudStack API.</div>        </td></tr>
                <tr><td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div>        </td></tr>
                <tr><td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Secret key of the CloudStack API.</div>        </td></tr>
                <tr><td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>HTTP timeout.</div>        </td></tr>
                <tr><td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div>        </td></tr>
                <tr><td>cidr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0.0.0.0/0</td>
        <td></td>
        <td><div>CIDR (full notation) to be used for firewall rule.</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Domain the firewall rule is related to.</div>        </td></tr>
                <tr><td>end_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>End port for this rule. Considered if <code>protocol=tcp</code> or <code>protocol=udp</code>. If not specified, equal <code>start_port</code>.</div>        </td></tr>
                <tr><td>icmp_code<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Error code for this icmp message. Considered if <code>protocol=icmp</code>.</div>        </td></tr>
                <tr><td>icmp_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Type of the icmp message being sent. Considered if <code>protocol=icmp</code>.</div>        </td></tr>
                <tr><td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Public IP address the ingress rule is assigned to.</div><div>Required if <code>type=ingress</code>.</div>        </td></tr>
                <tr><td>network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Network the egress rule is related to.</div><div>Required if <code>type=egress</code>.</div>        </td></tr>
                <tr><td>poll_async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Poll async jobs until job has finished.</div>        </td></tr>
                <tr><td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the project the firewall rule is related to.</div>        </td></tr>
                <tr><td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>tcp</li><li>udp</li><li>icmp</li><li>all</li></ul></td>
        <td><div>Protocol of the firewall rule.</div><div><code>all</code> is only available if <code>type=egress</code></div>        </td></tr>
                <tr><td>start_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Start port for this rule. Considered if <code>protocol=tcp</code> or <code>protocol=udp</code>.</div></br>
    <div style="font-size: small;">aliases: port<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the firewall rule.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ingress</td>
        <td><ul><li>ingress</li><li>egress</li></ul></td>
        <td><div>Type of the firewall rule.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the zone in which the virtual machine is in.</div><div>If not set, default zone is used.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Allow inbound port 80/tcp from 1.2.3.4 to 4.3.2.1
    - local_action:
        module: cs_firewall
        ip_address: 4.3.2.1
        port: 80
        cidr: 1.2.3.4/32
    
    # Allow inbound tcp/udp port 53 to 4.3.2.1
    - local_action:
        module: cs_firewall
        ip_address: 4.3.2.1
        port: 53
        protocol: '{{ item }}'
      with_items:
      - tcp
      - udp
    
    # Ensure firewall rule is removed
    - local_action:
        module: cs_firewall
        ip_address: 4.3.2.1
        start_port: 8000
        end_port: 8888
        cidr: 17.0.0.0/8
        state: absent
    
    # Allow all outbound traffic
    - local_action:
        module: cs_firewall
        network: my_network
        type: egress
        protocol: all
    
    # Allow only HTTP outbound traffic for an IP
    - local_action:
        module: cs_firewall
        network: my_network
        type: egress
        port: 80
        cidr: 10.101.1.20

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
        <td> icmp_code </td>
        <td> ICMP code of the rule. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 1 </td>
    </tr>
            <tr>
        <td> start_port </td>
        <td> Start port of the rule. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 80 </td>
    </tr>
            <tr>
        <td> network </td>
        <td> Name of the network if C(type=egress) </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> my_network </td>
    </tr>
            <tr>
        <td> type </td>
        <td> Type of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ingress </td>
    </tr>
            <tr>
        <td> end_port </td>
        <td> End port of the rule. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 80 </td>
    </tr>
            <tr>
        <td> protocol </td>
        <td> Protocol of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> tcp </td>
    </tr>
            <tr>
        <td> cidr </td>
        <td> CIDR of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 0.0.0.0/0 </td>
    </tr>
            <tr>
        <td> icmp_type </td>
        <td> ICMP type of the rule. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 1 </td>
    </tr>
            <tr>
        <td> ip_address </td>
        <td> IP address of the rule if C(type=ingress) </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.100.212.10 </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 04589590-ac63-4ffc-93f5-b698b8ac38b6 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
    - A detailed guide about cloudstack modules can be found on http://docs.ansible.com/ansible/guide_cloudstack.html
    - This module supports check mode.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
