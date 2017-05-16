.. _riak:


riak - This module handles some common Riak operations
++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module can be used to join nodes to a cluster, check the status of the cluster.




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
                <tr><td>command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>ping</li><li>kv_test</li><li>join</li><li>plan</li><li>commit</li></ul></td>
        <td><div>The command you would like to perform against the cluster.</div>        </td></tr>
                <tr><td>config_dir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/riak</td>
        <td></td>
        <td><div>The path to the riak configuration directory</div>        </td></tr>
                <tr><td>http_conn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>127.0.0.1:8098</td>
        <td></td>
        <td><div>The ip address and port that is listening for Riak HTTP queries</div>        </td></tr>
                <tr><td>target_node<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>riak@127.0.0.1</td>
        <td></td>
        <td><div>The target node for certain operations (join, ping)</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
                <tr><td>wait_for_handoffs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of seconds to wait for handoffs to complete.</div>        </td></tr>
                <tr><td>wait_for_ring<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of seconds to wait for all nodes to agree on the ring.</div>        </td></tr>
                <tr><td>wait_for_service<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>kv</li></ul></td>
        <td><div>Waits for a riak service to come online before continuing.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Join's a Riak node to another node
    - riak:
        command: join
        target_node: riak@10.1.1.1
    
    # Wait for handoffs to finish.  Use with async and poll.
    - riak:
        wait_for_handoffs: yes
    
    # Wait for riak_kv service to startup
    - riak:
        wait_for_service: kv





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
