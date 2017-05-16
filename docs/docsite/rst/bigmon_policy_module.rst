.. _bigmon_policy:


bigmon_policy - Create and remove a bigmon out-of-band policy.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create and remove a bigmon out-of-band policy.




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
                <tr><td>access_token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Bigmon access token. If this isn't set the the environment variable <code>BIGSWITCH_ACCESS_TOKEN</code> is used.</div>        </td></tr>
                <tr><td>action<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>forward</td>
        <td><ul><li>forward</li><li>drop</li><li>flow-gen</li></ul></td>
        <td><div>Forward matching packets to delivery interfaces, Drop is for measure rate of matching packets, but do not forward to delivery interfaces, capture packets and write to a PCAP file, or enable NetFlow generation.</div>        </td></tr>
                <tr><td>controller<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The controller address.</div>        </td></tr>
                <tr><td>delivery_packet_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Run policy until delivery_packet_count packets are delivered.</div>        </td></tr>
                <tr><td>duration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Run policy for duration duration or until delivery_packet_count packets are delivered, whichever comes first.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the policy.</div>        </td></tr>
                <tr><td>policy_description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of policy.</div>        </td></tr>
                <tr><td>priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>100</td>
        <td></td>
        <td><div>A priority associated with this policy. The higher priority policy takes precedence over a lower priority.</div>        </td></tr>
                <tr><td>start_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ansible_date_time.iso8601</td>
        <td></td>
        <td><div>Date the policy becomes active</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the policy should be present or absent.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If <code>false</code>, SSL certificates will not be validated. This should only be used on personally controlled devices using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: policy to aggregate filter and deliver data center (DC) 1 traffic
      bigmon_policy:
        name: policy1
        policy_description: DC 1 traffic policy
        action: drop
        controller: '{{ inventory_hostname }}'
        state: present
        validate_certs: false





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
