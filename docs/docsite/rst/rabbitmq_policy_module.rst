.. _rabbitmq_policy:


rabbitmq_policy - Manage the state of policies in RabbitMQ.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage the state of a virtual host in RabbitMQ.




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
                <tr><td>apply_to<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>all</td>
        <td><ul><li>all</li><li>exchanges</li><li>queues</li></ul></td>
        <td><div>What the policy applies to. Requires RabbitMQ 3.2.0 or later.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the policy to manage.</div>        </td></tr>
                <tr><td>node<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>rabbit</td>
        <td></td>
        <td><div>Erlang node name of the rabbit we wish to configure.</div>        </td></tr>
                <tr><td>pattern<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A regex of queues to apply the policy to.</div>        </td></tr>
                <tr><td>priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The priority of the policy.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The state of the policy.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A dict or string describing the policy.</div>        </td></tr>
                <tr><td>vhost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/</td>
        <td></td>
        <td><div>The name of the vhost to apply to.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: ensure the default vhost contains the HA policy via a dict
      rabbitmq_policy:
        name: HA
        pattern: .*
      args:
        tags:
          ha-mode: all
    
    - name: ensure the default vhost contains the HA policy
      rabbitmq_policy:
        name: HA
        pattern: .*
        tags:
          ha-mode: all





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
