.. _cs_securitygroup_rule:


cs_securitygroup_rule - Manages security group rules on Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add and remove security group rules.


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
    <td>cidr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0.0.0.0/0</td>
        <td><ul></ul></td>
        <td><div>CIDR (full notation) to be used for security group rule.</div></td></tr>
            <tr>
    <td>end_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>End port for this rule. Required if <code>protocol=tcp</code> or <code>protocol=udp</code>, but <code>start_port</code> will be used if not set.</div></td></tr>
            <tr>
    <td>icmp_code<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Error code for this icmp message. Required if <code>protocol=icmp</code>.</div></td></tr>
            <tr>
    <td>icmp_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Type of the icmp message being sent. Required if <code>protocol=icmp</code>.</div></td></tr>
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
        <td><div>Name of the project the security group to be created in.</div></td></tr>
            <tr>
    <td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>tcp</li><li>udp</li><li>icmp</li><li>ah</li><li>esp</li><li>gre</li></ul></td>
        <td><div>Protocol of the security group rule.</div></td></tr>
            <tr>
    <td>security_group<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the security group the rule is related to. The security group must be existing.</div></td></tr>
            <tr>
    <td>start_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Start port for this rule. Required if <code>protocol=tcp</code> or <code>protocol=udp</code>.</div></br>
        <div style="font-size: small;">aliases: port<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the security group rule.</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ingress</td>
        <td><ul><li>ingress</li><li>egress</li></ul></td>
        <td><div>Ingress or egress security group rule.</div></td></tr>
            <tr>
    <td>user_security_group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Security group this rule is based of.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # Allow inbound port 80/tcp from 1.2.3.4 added to security group 'default'
    - local_action:
        module: cs_securitygroup_rule
        security_group: default
        port: 80
        cidr: 1.2.3.4/32
    
    # Allow tcp/udp outbound added to security group 'default'
    - local_action:
        module: cs_securitygroup_rule
        security_group: default
        type: egress
        start_port: 1
        end_port: 65535
        protocol: '{{ item }}'
      with_items:
      - tcp
      - udp
    
    # Allow inbound icmp from 0.0.0.0/0 added to security group 'default'
    - local_action:
        module: cs_securitygroup_rule
        security_group: default
        protocol: icmp
        icmp_code: -1
        icmp_type: -1
    
    # Remove rule inbound port 80/tcp from 0.0.0.0/0 from security group 'default'
    - local_action:
        module: cs_securitygroup_rule
        security_group: default
        port: 80
        state: absent
    
    # Allow inbound port 80/tcp from security group web added to security group 'default'
    - local_action:
        module: cs_securitygroup_rule
        security_group: default
        port: 80
        user_security_group: web

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
        <td> protocol </td>
        <td> protocol of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> tcp </td>
    </tr>
            <tr>
        <td> user_security_group </td>
        <td> user security group of the rule. </td>
        <td align=center> success and user_security_group is defined </td>
        <td align=center> string </td>
        <td align=center> default </td>
    </tr>
            <tr>
        <td> end_port </td>
        <td> end port of the rule. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 80 </td>
    </tr>
            <tr>
        <td> security_group </td>
        <td> security group of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> default </td>
    </tr>
            <tr>
        <td> start_port </td>
        <td> start port of the rule. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 80 </td>
    </tr>
            <tr>
        <td> cidr </td>
        <td> CIDR of the rule. </td>
        <td align=center> success and cidr is defined </td>
        <td align=center> string </td>
        <td align=center> 0.0.0.0/0 </td>
    </tr>
            <tr>
        <td> type </td>
        <td> type of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ingress </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> a6f7a5fc-43f8-11e5-a151-feff819cdc9f </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
.. note:: This module supports check mode.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

