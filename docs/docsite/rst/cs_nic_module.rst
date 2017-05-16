.. _cs_nic:


cs_nic - Manages NICs and secondary IPs of an instance on Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add and remove secondary IPs to and from a NIC.


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
        <td><div>Account the instance is related to.</div>        </td></tr>
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
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Domain the instance is related to.</div>        </td></tr>
                <tr><td>network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the network.</div><div>Required to find the NIC if instance has multiple networks assigned.</div>        </td></tr>
                <tr><td>poll_async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Poll async jobs until job has finished.</div>        </td></tr>
                <tr><td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the project the instance is deployed in.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the ipaddress.</div>        </td></tr>
                <tr><td>vm<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of instance.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>vm_guest_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Secondary IP address to be added to the instance nic.</div><div>If not set, the API always returns a new IP address and idempotency is not given.</div></br>
    <div style="font-size: small;">aliases: secondary_ip<div>        </td></tr>
                <tr><td>vpc<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the VPC the <code>vm</code> is related to.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the zone in which the instance is deployed in.</div><div>If not set, default zone is used.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Assign a specific IP to the default NIC of the VM
    - local_action:
        module: cs_nic
        vm: customer_xy
        vm_guest_ip: 10.10.10.10
    
    # Assign an IP to the default NIC of the VM
    # Note: If vm_guest_ip is not set, you will get a new IP address on every run.
    - local_action:
        module: cs_nic
        vm: customer_xy
    
    # Remove a specific IP from the default NIC
    - local_action:
        module: cs_nic
        vm: customer_xy
        vm_guest_ip: 10.10.10.10
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
        <td> vm_guest_ip </td>
        <td> Secondary IP of the NIC. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.10.10.10 </td>
    </tr>
            <tr>
        <td> domain </td>
        <td> Domain the VM is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> network </td>
        <td> Name of the network if not default. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> sync network </td>
    </tr>
            <tr>
        <td> vm </td>
        <td> Name of the VM. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web-01 </td>
    </tr>
            <tr>
        <td> project </td>
        <td> Name of project the VM is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Production </td>
    </tr>
            <tr>
        <td> netmask </td>
        <td> Netmask of the NIC. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 255.255.255.0 </td>
    </tr>
            <tr>
        <td> mac_address </td>
        <td> MAC address of the NIC. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 02:00:33:31:00:e4 </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the VM is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> ip_address </td>
        <td> Primary IP of the NIC. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.10.10.10 </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the nic. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 87b1e0ce-4e01-11e4-bb66-0050569e64b8 </td>
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
