.. _influxdb_database:


influxdb_database - Manage InfluxDB databases
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage InfluxDB databases


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
        <td><div>Name of the database that will be created/destroyed</div>        </td></tr>
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
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>8086</td>
        <td></td>
        <td><div>The port on which InfluxDB server is listening</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Determines if the database should be created or destroyed</div>        </td></tr>
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

    # Example influxdb_database command from Ansible Playbooks
    - name: Create database
      influxdb_database:
          hostname: "{{influxdb_ip_address}}"
          database_name: "{{influxdb_database_name}}"
          state: present
    
    - name: Destroy database
      influxdb_database:
          hostname: "{{influxdb_ip_address}}"
          database_name: "{{influxdb_database_name}}"
          state: absent
    
    - name: Create database using custom credentials
      influxdb_database:
          hostname: "{{influxdb_ip_address}}"
          username: "{{influxdb_username}}"
          password: "{{influxdb_password}}"
          database_name: "{{influxdb_database_name}}"
          state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
