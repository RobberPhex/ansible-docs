.. _junos_template:


junos_template - Manage configuration on remote devices running Junos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`junos_template <junos_template>` module will load a candidate configuration from a template file onto a remote device running Junos.  The module will return the differences in configuration if the diff option is specified on the Ansible command line


Requirements (on host that executes module)
-------------------------------------------

  * junos-eznc


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
    <td>action<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>merge</td>
        <td><ul><li>merge</li><li>overwrite</li><li>replace</li></ul></td>
        <td><div>The <code>action</code> argument specifies how the module will apply changes.</div></td></tr>
            <tr>
    <td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>When this argument is configured true, the module will backup the configuration from the node prior to making any changes. The backup file will be written to backup_{{ hostname }} in the root of the playbook directory.</div></td></tr>
            <tr>
    <td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>configured by junos_template</td>
        <td><ul></ul></td>
        <td><div>The <code>comment</code> argument specifies a text string to be used when committing the configuration.  If the <code>confirm</code> argument is set to False, this argument is silently ignored.</div></td></tr>
            <tr>
    <td>config_format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>text</li><li>xml</li><li>set</li></ul></td>
        <td><div>The <code>format</code> argument specifies the format of the configuration template specified in <code>src</code>.  If the format argument is not specified, the module will attempt to infer the configuration format based of file extension.  Files that end in <em>xml</em> will set the format to xml.  Files that end in <em>set</em> will set the format to set and all other files will default the format to text.</div></td></tr>
            <tr>
    <td>confirm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>confirm</code> argument will configure a time out value for the commit to be confirmed before it is automatically rolled back.  If the <code>confirm</code> argument is set to False, this argument is silently ignored.  If the value for this argument is set to 0, the commit is confirmed immediately.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.   The value of <em>password</em> is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_PASSWORD will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>22</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when buiding the connection to the remote device.  The port value will default to the well known SSH port of 22</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convience method that allows all <span class='module'>ios</span> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to the config source.  The source can be either a file with config or a template that will be merged during runtime.  By default the task will search for the source file in role or playbook root folder in templates directory.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.   The value of <em>ssh_keyfile</em> is the path to the key used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_SSH_KEYFILE will be used instead.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the usename to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_USERNAME will be used instead.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - junos_template:
        src: config.j2
        comment: update system config
    
    - name: replace config hierarchy
        src: config.j2
        action: replace
    
    - name: overwrite the config
        src: config.j2
        action: overwrite


Notes
-----

.. note:: This module requires the netconf system service be enabled on the remote device being managed


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

