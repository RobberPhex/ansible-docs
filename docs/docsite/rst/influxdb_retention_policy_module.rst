.. _influxdb_retention_policy:


influxdb_retention_policy - Manage InfluxDB retention policies
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage InfluxDB retention policies


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * influxdb >= 0.9


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
                <tr><td>database_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the database where retention policy will be created</div>        </td></tr>
                <tr><td>default<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Sets the retention policy as default retention policy</div>        </td></tr>
                <tr><td>duration<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Determines how long InfluxDB should keep the data</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address on which InfluxDB server is listening</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>root</td>
        <td></td>
        <td><div>Password that will be used to authenticate against InfluxDB server</div>        </td></tr>
                <tr><td>policy_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the retention policy</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>8086</td>
        <td></td>
        <td><div>The port on which InfluxDB server is listening</div>        </td></tr>
                <tr><td>replication<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Determines how many independent copies of each point are stored in the cluster</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>root</td>
        <td></td>
        <td><div>Username that will be used to authenticate against InfluxDB server</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example influxdb_retention_policy command from Ansible Playbooks
    - name: create 1 hour retention policy
      influxdb_retention_policy:
          hostname: "{{influxdb_ip_address}}"
          database_name: "{{influxdb_database_name}}"
          policy_name: test
          duration: 1h
          replication: 1
    
    - name: create 1 day retention policy
      influxdb_retention_policy:
          hostname: "{{influxdb_ip_address}}"
          database_name: "{{influxdb_database_name}}"
          policy_name: test
          duration: 1d
          replication: 1
    
    - name: create 1 week retention policy
      influxdb_retention_policy:
          hostname: "{{influxdb_ip_address}}"
          database_name: "{{influxdb_database_name}}"
          policy_name: test
          duration: 1w
          replication: 1
    
    - name: create infinite retention policy
      influxdb_retention_policy:
          hostname: "{{influxdb_ip_address}}"
          database_name: "{{influxdb_database_name}}"
          policy_name: test
          duration: INF
          replication: 1





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
