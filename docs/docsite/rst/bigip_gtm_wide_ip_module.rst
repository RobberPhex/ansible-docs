.. _bigip_gtm_wide_ip:


bigip_gtm_wide_ip - Manages F5 BIG-IP GTM wide ip
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages F5 BIG-IP GTM wide ip


Requirements (on host that executes module)
-------------------------------------------

  * bigsuds


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
                <tr><td>lb_method<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>return_to_dns</li><li>null</li><li>round_robin</li><li>ratio</li><li>topology</li><li>static_persist</li><li>global_availability</li><li>vs_capacity</li><li>least_conn</li><li>lowest_rtt</li><li>lowest_hops</li><li>packet_rate</li><li>cpu</li><li>hit_ratio</li><li>qos</li><li>bps</li><li>drop_packet</li><li>explicit_ip</li><li>connection_rate</li><li>vs_score</li></ul></td>
        <td><div>LB method of wide ip</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password for the user account used to connect to the BIG-IP. This option can be omitted if the environment variable <code>F5_PASSWORD</code> is set.</div>        </td></tr>
                <tr><td>server<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The BIG-IP host. This option can be omitted if the environment variable <code>F5_SERVER</code> is set.</div>        </td></tr>
                <tr><td>server_port<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>443</td>
        <td></td>
        <td><div>The BIG-IP server port. This option can be omitted if the environment variable <code>F5_SERVER_PORT</code> is set.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username to connect to the BIG-IP with. This user must have administrative privileges on the device. This option can be omitted if the environment variable <code>F5_USER</code> is set.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates. This option can be omitted if the environment variable <code>F5_VALIDATE_CERTS</code> is set.</div>        </td></tr>
                <tr><td>wide_ip<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Wide IP name</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      - name: Set lb method
        local_action: >
          bigip_gtm_wide_ip
          server=192.0.2.1
          user=admin
          password=mysecret
          lb_method=round_robin
          wide_ip=my-wide-ip.example.com


Notes
-----

.. note::
    - Requires BIG-IP software version >= 11.4
    - F5 developed module 'bigsuds' required (see http://devcentral.f5.com)
    - Best run as a local_action in your playbook
    - Tested with manager and above account privilege level



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
