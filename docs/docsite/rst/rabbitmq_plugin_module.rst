.. _rabbitmq_plugin:


rabbitmq_plugin - Adds or removes plugins to RabbitMQ
+++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Enables or disables RabbitMQ plugins




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
                <tr><td>names<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Comma-separated list of plugin names</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>new_only<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Only enable missing plugins</div><div>Does not disable plugins that are not in the names list</div>        </td></tr>
                <tr><td>prefix<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a custom install prefix to a Rabbit</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>enabled</td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td><div>Specify if plugins are to be enabled or disabled</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Enables the rabbitmq_management plugin
    - rabbitmq_plugin:
        names: rabbitmq_management
        state: enabled





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
