.. _fortios_config:


fortios_config - Manage config on Fortinet FortiOS firewall devices
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module provides management of FortiOS Devices configuration.




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
                <tr><td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This argument will cause the module to create a backup of the current <code>running-config</code> from the remote device before any changes are made.  The backup file is written to the i(backup) folder.</div>        </td></tr>
                <tr><td>backup_filename<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the backup filename. If omitted filename will be formated like HOST_config.YYYY-MM-DD@HH:MM:SS</div>        </td></tr>
                <tr><td>backup_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies where to store backup files. Required if <em>backup=yes</em>.</div>        </td></tr>
                <tr><td>filter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Only for partial backup, you can restrict by giving expected configuration path (ex. firewall address).</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the DNS hostname or IP address for connecting to the remote fortios device.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the password used to authenticate to the remote device.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The <em>src</em> argument provides a path to the configuration file to load into the remote device.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>60</td>
        <td></td>
        <td><div>Timeout in seconds for connecting to the remote device.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Configures the username used to authenticate to the remote device.</div>        </td></tr>
                <tr><td>vdom<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies on which vdom to apply configuration</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Backup current config
      fortios_config:
        host: 192.168.0.254
        username: admin
        password: password
        backup: yes
    
    - name: Backup only address objects
      fortios_config:
        host: 192.168.0.254
        username: admin
        password: password
        backup: yes
        backup_path: /tmp/forti_backup/
        filter: "firewall address"
    
    - name: Update configuration from file
      fortios_config:
        host: 192.168.0.254
        username: admin
        password: password
        src: new_configuration.conf
    

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
        <td> running_config </td>
        <td> full config string </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> change_string </td>
        <td> The commands really executed by the module </td>
        <td align=center> only if config changed </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - This module requires pyFG python library



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
