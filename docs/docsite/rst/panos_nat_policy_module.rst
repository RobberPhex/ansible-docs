.. _panos_nat_policy:


panos_nat_policy - create a policy NAT rule
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create a policy nat rule. Keep in mind that we can either end up configuring source NAT, destination NAT, or both. Instead of splitting it into two we will make a fair attempt to determine which one the user wants.


Requirements (on host that executes module)
-------------------------------------------

  * pan-python


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
                <tr><td>commit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>commit if changed</div>        </td></tr>
                <tr><td>destination<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'any']</td>
        <td></td>
        <td><div>list of destination addresses</div>        </td></tr>
                <tr><td>dnat_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>dnat translated address</div>        </td></tr>
                <tr><td>dnat_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>dnat translated port</div>        </td></tr>
                <tr><td>from_zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>list of source zones</div>        </td></tr>
                <tr><td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>IP address (or hostname) of PAN-OS device</div>        </td></tr>
                <tr><td>override<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>false</td>
        <td></td>
        <td><div>attempt to override rule if one with the same name already exists</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>password for authentication</div>        </td></tr>
                <tr><td>rule_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>name of the SNAT rule</div>        </td></tr>
                <tr><td>service<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>any</td>
        <td></td>
        <td><div>service</div>        </td></tr>
                <tr><td>snat_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>snat translated address</div>        </td></tr>
                <tr><td>snat_bidirectional<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>false</td>
        <td></td>
        <td><div>bidirectional flag</div>        </td></tr>
                <tr><td>snat_interface<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>snat interface</div>        </td></tr>
                <tr><td>snat_interface_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>snat interface address</div>        </td></tr>
                <tr><td>snat_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>type of source translation</div>        </td></tr>
                <tr><td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'any']</td>
        <td></td>
        <td><div>list of source addresses</div>        </td></tr>
                <tr><td>to_zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>destination zone</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>username for authentication</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a source and destination nat rule
      - name: create nat SSH221 rule for 10.0.1.101
        panos_nat:
          ip_address: "192.168.1.1"
          password: "admin"
          rule_name: "Web SSH"
          from_zone: ["external"]
          to_zone: "external"
          source: ["any"]
          destination: ["10.0.0.100"]
          service: "service-tcp-221"
          snat_type: "dynamic-ip-and-port"
          snat_interface: "ethernet1/2"
          dnat_address: "10.0.1.101"
          dnat_port: "22"
          commit: False





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
