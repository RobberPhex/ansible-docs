.. _elasticsearch_plugin:


elasticsearch_plugin - Manage Elasticsearch plugins
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages Elasticsearch plugins.




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
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the plugin to install. In ES 2.x, the name can be an url or file location</div></td></tr>
            <tr>
    <td>plugin_bin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/usr/share/elasticsearch/bin/plugin</td>
        <td><ul></ul></td>
        <td><div>Location of the plugin binary</div></td></tr>
            <tr>
    <td>plugin_dir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/usr/share/elasticsearch/plugins/</td>
        <td><ul></ul></td>
        <td><div>Your configured plugin directory specified in Elasticsearch</div></td></tr>
            <tr>
    <td>proxy_host<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Proxy host to use during plugin installation</div></td></tr>
            <tr>
    <td>proxy_port<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Proxy port to use during plugin installation</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Desired state of a plugin.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1m</td>
        <td><ul></ul></td>
        <td><div>Timeout setting: 30s, 1m, 1h...</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Set exact URL to download the plugin from (Only works for ES 1.x)</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Version of the plugin to be installed. If plugin exists with previous version, it will NOT be updated</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install Elasticsearch head plugin
    - elasticsearch_plugin: state=present name="mobz/elasticsearch-head"
    
    # Install specific version of a plugin
    - elasticsearch_plugin: state=present name="com.github.kzwang/elasticsearch-image" version="1.2.0"
    
    # Uninstall Elasticsearch head plugin
    - elasticsearch_plugin: state=absent name="mobz/elasticsearch-head"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

