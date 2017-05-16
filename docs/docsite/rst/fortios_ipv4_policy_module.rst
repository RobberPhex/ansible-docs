.. _fortios_ipv4_policy:


fortios_ipv4_policy - Manage IPv4 policy objects on Fortinet FortiOS firewall devices
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module provides management of firewall IPv4 policies on FortiOS devices.




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
                <tr><td>application_list<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies Application Control name.</div>        </td></tr>
                <tr><td>av_profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies Antivirus profile name.</div>        </td></tr>
                <tr><td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This argument will cause the module to create a backup of the current <code>running-config</code> from the remote device before any changes are made.  The backup file is written to the i(backup) folder.</div>        </td></tr>
                <tr><td>backup_filename<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the backup filename. If omitted filename will be formated like HOST_config.YYYY-MM-DD@HH:MM:SS</div>        </td></tr>
                <tr><td>backup_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies where to store backup files. Required if <em>backup=yes</em>.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>free text to describe policy.</div>        </td></tr>
                <tr><td>dst_addr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies destination address (or group) object name(s). Required when <em>state=present</em>.</div>        </td></tr>
                <tr><td>dst_addr_negate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Negate destination address param.</div>        </td></tr>
                <tr><td>dst_intf<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>any</td>
        <td></td>
        <td><div>Specifies destination interface name.</div>        </td></tr>
                <tr><td>fixedport<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Use fixed port for nat.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the DNS hostname or IP address for connecting to the remote fortios device.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Policy ID. Warning: policy ID number is different than Policy sequence number. The policy ID is the number assigned at policy creation. The sequence number represents the order in which the Fortigate will evaluate the rule for policy enforcement, and also the order in which rules are listed in the GUI and CLI. These two numbers do not necessarily correlate: this module is based off policy ID. TIP: policy ID can be viewed in the GUI by adding 'ID' to the display columns</div>        </td></tr>
                <tr><td>ips_sensor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies IPS Sensor profile name.</div>        </td></tr>
                <tr><td>nat<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enable or disable Nat.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the password used to authenticate to the remote device.</div>        </td></tr>
                <tr><td>policy_action<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>accept</li><li>deny</li></ul></td>
        <td><div>Specifies accept or deny action policy. Required when <em>state=present</em>.</div></br>
    <div style="font-size: small;">aliases: action<div>        </td></tr>
                <tr><td>poolname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies NAT pool name.</div>        </td></tr>
                <tr><td>schedule<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>always</td>
        <td></td>
        <td><div>defines policy schedule.</div>        </td></tr>
                <tr><td>service<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies policy service(s), could be a list (ex: ['MAIL','DNS']). Required when <em>state=present</em>.</div></br>
    <div style="font-size: small;">aliases: services<div>        </td></tr>
                <tr><td>service_negate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Negate policy service(s) defined in service value.</div>        </td></tr>
                <tr><td>src_addr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies source address (or group) object name(s). Required when <em>state=present</em>.</div>        </td></tr>
                <tr><td>src_addr_negate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Negate source address param.</div>        </td></tr>
                <tr><td>src_intf<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>any</td>
        <td></td>
        <td><div>Specifies source interface name.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Specifies if policy <em>id</em> need to be added or deleted.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>60</td>
        <td></td>
        <td><div>Timeout in seconds for connecting to the remote device.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Configures the username used to authenticate to the remote device.</div>        </td></tr>
                <tr><td>vdom<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies on which vdom to apply configuration</div>        </td></tr>
                <tr><td>webfilter_profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies Webfilter profile name.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Allow external DNS call
      fortios_ipv4_policy:
        host: 192.168.0.254
        username: admin
        password: password
        id: 42
        srcaddr: internal_network
        dstaddr: all
        service: dns
        nat: True
        state: present
        policy_action: accept
    
    - name: Public Web
      fortios_ipv4_policy:
        host: 192.168.0.254
        username: admin
        password: password
        id: 42
        srcaddr: all
        dstaddr: webservers
        services:
          - http
          - https
        state: present
        policy_action: accept

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
        <td> firewall_address_config </td>
        <td> full firewall adresses config string </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> change_string </td>
        <td> The commands executed by the module </td>
        <td align=center> only if config changed </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> msg_error_list </td>
        <td> List of errors returned by CLI (use -vvv for better readability). </td>
        <td align=center> only when error </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - This module requires pyFG library.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
