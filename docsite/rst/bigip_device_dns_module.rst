.. _bigip_device_dns:


bigip_device_dns - Manage BIG-IP device DNS settings
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage BIG-IP device DNS settings


Requirements (on host that executes module)
-------------------------------------------

  * f5-sdk


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
    <td>cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>disable</td>
        <td><ul><li>enable</li><li>disable</li></ul></td>
        <td><div>Specifies whether the system caches DNS lookups or performs the operation each time a lookup is needed. Please note that this applies only to Access Policy Manager features, such as ACLs, web application rewrites, and authentication.</div></td></tr>
            <tr>
    <td>forwarders<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of BIND servers that the system can use to perform DNS lookups</div></td></tr>
            <tr>
    <td>ip_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>4</li><li>6</li></ul></td>
        <td><div>Specifies whether the DNS specifies IP addresses using IPv4 or IPv6.</div></td></tr>
            <tr>
    <td>name_servers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of name serverz that the system uses to validate DNS lookups</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password for the user account used to connect to the BIG-IP.</div></td></tr>
            <tr>
    <td>search<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of domains that the system searches for local domain lookups, to resolve local host names.</div></td></tr>
            <tr>
    <td>server<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The BIG-IP host.</div></td></tr>
            <tr>
    <td>server_port<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>443</td>
        <td><ul></ul></td>
        <td><div>The BIG-IP server port.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>The state of the variable on the system. When <code>present</code>, guarantees that an existing variable is set to <code>value</code>.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username to connect to the BIG-IP with. This user must have administrative privileges on the device.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Set the DNS settings on the BIG-IP
      bigip_device_dns:
          name_servers:
              - 208.67.222.222
              - 208.67.220.220
          search:
              - localdomain
              - lab.local
          state: present
          password: "secret"
          server: "lb.mydomain.com"
          user: "admin"
          validate_certs: "no"
      delegate_to: localhost

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
        <td> name_servers </td>
        <td> List of name servers that were added or removed </td>
        <td align=center> changed </td>
        <td align=center> list </td>
        <td align=center> ['192.0.2.10', '172.17.12.10'] </td>
    </tr>
            <tr>
        <td> ip_version </td>
        <td> IP version that was set that DNS will specify IP addresses in </td>
        <td align=center> changed </td>
        <td align=center> int </td>
        <td align=center> 4 </td>
    </tr>
            <tr>
        <td> search </td>
        <td> List of search domains that were added or removed </td>
        <td align=center> changed </td>
        <td align=center> list </td>
        <td align=center> ['192.0.2.10', '172.17.12.10'] </td>
    </tr>
            <tr>
        <td> cache </td>
        <td> The new value of the DNS caching </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> enabled </td>
    </tr>
            <tr>
        <td> forwarders </td>
        <td> List of forwarders that were added or removed </td>
        <td align=center> changed </td>
        <td align=center> list </td>
        <td align=center> ['192.0.2.10', '172.17.12.10'] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Requires the f5-sdk Python package on the host. This is as easy as pip install requests


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

