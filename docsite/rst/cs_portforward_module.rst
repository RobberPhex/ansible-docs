.. _cs_portforward:


cs_portforward - Manages port forwarding rules on Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update and remove port forwarding rules.


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
        <td><div>Account the <code>vm</code> is related to.</div></td></tr>
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
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Domain the <code>vm</code> is related to.</div></td></tr>
            <tr>
    <td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Public IP address the rule is assigned to.</div></td></tr>
            <tr>
    <td>open_firewall<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether the firewall rule for public port should be created, while creating the new rule.</div><div>Use <span class='module'>cs_firewall</span> for managing firewall rules.</div></td></tr>
            <tr>
    <td>poll_async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Poll async jobs until job has finished.</div></td></tr>
            <tr>
    <td>private_end_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>End private port for this rule.</div><div>If not specified equal <code>private_port</code>.</div></td></tr>
            <tr>
    <td>private_port<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Start private port for this rule.</div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the project the <code>vm</code> is located in.</div></td></tr>
            <tr>
    <td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>tcp</li><li>udp</li></ul></td>
        <td><div>Protocol of the port forwarding rule.</div></td></tr>
            <tr>
    <td>public_end_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>End public port for this rule.</div><div>If not specified equal <code>public_port</code>.</div></td></tr>
            <tr>
    <td>public_port<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Start public port for this rule.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the port forwarding rule.</div></td></tr>
            <tr>
    <td>vm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of virtual machine which we make the port forwarding rule for.</div><div>Required if <code>state=present</code>.</div></td></tr>
            <tr>
    <td>vm_guest_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>VM guest NIC secondary IP address for the port forwarding rule.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the zone in which the virtual machine is in.</div><div>If not set, default zone is used.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # 1.2.3.4:80 -> web01:8080
    - local_action:
        module: cs_portforward
        ip_address: 1.2.3.4
        vm: web01
        public_port: 80
        private_port: 8080
    
    # forward SSH and open firewall
    - local_action:
        module: cs_portforward
        ip_address: '{{ public_ip }}'
        vm: '{{ inventory_hostname }}'
        public_port: '{{ ansible_ssh_port }}'
        private_port: 22
        open_firewall: true
    
    # forward DNS traffic, but do not open firewall
    - local_action:
        module: cs_portforward
        ip_address: 1.2.3.4
        vm: '{{ inventory_hostname }}'
        public_port: 53
        private_port: 53
        protocol: udp
    
    # remove ssh port forwarding
    - local_action:
        module: cs_portforward
        ip_address: 1.2.3.4
        public_port: 22
        private_port: 22
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
        <td> vm_name </td>
        <td> Name of the virtual machine. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web-01 </td>
    </tr>
            <tr>
        <td> vm_display_name </td>
        <td> Display name of the virtual machine. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web-01 </td>
    </tr>
            <tr>
        <td> protocol </td>
        <td> Protocol. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> tcp </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> Tags related to the port forwarding. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [] </td>
    </tr>
            <tr>
        <td> public_port </td>
        <td> Start port on the public IP address. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 80 </td>
    </tr>
            <tr>
        <td> public_end_port </td>
        <td> End port on the public IP address. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 80 </td>
    </tr>
            <tr>
        <td> private_port </td>
        <td> Start port on the virtual machine's IP address. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 80 </td>
    </tr>
            <tr>
        <td> private_end_port </td>
        <td> End port on the virtual machine's IP address. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ip_address </td>
        <td> Public IP address. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.2.3.4 </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the public IP address. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> a6f7a5fc-43f8-11e5-a151-feff819cdc9f </td>
    </tr>
            <tr>
        <td> vm_guest_ip </td>
        <td> IP of the virtual machine. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.101.65.152 </td>
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

