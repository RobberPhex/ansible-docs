.. _logstash_plugin:


logstash_plugin - Manage Logstash plugins
+++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages Logstash plugins.




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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Install plugin with that name.</div>        </td></tr>
                <tr><td>plugin_bin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/usr/share/logstash/bin/logstash-plugin</td>
        <td></td>
        <td><div>Specify logstash-plugin to use for plugin management.</div>        </td></tr>
                <tr><td>proxy_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Proxy host to use during plugin installation.</div>        </td></tr>
                <tr><td>proxy_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Proxy port to use during plugin installation.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Apply plugin state.</div>        </td></tr>
                <tr><td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Specify plugin Version of the plugin to install. If plugin exists with previous version, it will NOT be updated.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Install Logstash beats input plugin
      logstash_plugin:
        state: present
        name: logstash-input-beats
    
    - name: Install specific version of a plugin
      logstash_plugin:
        state: present
        name: logstash-input-syslog
        version: '3.2.0'
    
    - name: Uninstall Logstash plugin
      logstash_plugin:
        state: absent
        name: logstash-filter-multiline





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
