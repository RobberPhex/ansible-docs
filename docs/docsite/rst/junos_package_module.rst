.. _junos_package:


junos_package - Installs packages on remote devices running Junos
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module can install new and updated packages on remote devices running Junos.  The module will compare the specified package with the one running on the remote device and install the specified version if there is a mismatch


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
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>The <em>force</em> argument instructs the module to bypass the package version check and install the packaged identified in <em>src</em> on the remote device.</div>        </td></tr>
                <tr><td>no_copy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>The <em>no_copy</em> argument is responsible for instructing the remote device on where to install the package from.  When enabled, the package is transferred to the remote device prior to installing.</div>        </td></tr>
                <tr><td rowspan="2">provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td><td></td>
    <td> <div>A dict object containing connection details.</div>    </tr>
    <tr>
    <td colspan="5">
    <table border=1 cellpadding=4>
    <caption><b>Dictionary object provider</b></caption>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                    <tr><td>username<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Configures the username to use to authenticate the connection to the remote device.  This value is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div>        </td></tr>
                    <tr><td>host<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                    <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.   This value is the path to the key used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                    <tr><td>timeout<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>10</td>
                <td></td>
                <td><div>Specifies the timeout in seconds for communicating with the network device for either connecting or sending commands.  If the timeout is exceeded before the operation is completed, the module will error.</div>        </td></tr>
                    <tr><td>password<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the password to use to authenticate the connection to the remote device.   This value is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div>        </td></tr>
                    <tr><td>port<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>22</td>
                <td></td>
                <td><div>Specifies the port to use when building the connection to the remote device.  The port value will default to the well known SSH port of 22 (for <code>transport=cli</code>) or port 830 (for <code>transport=netconf</code>) device.</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>reboot<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>True</td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>In order for a package to take effect, the remote device must be restarted.  When enabled, this argument will instruct the module to reboot the device once the updated package has been installed. If disabled or the remote package does not need to be changed, the device will not be started.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The <em>src</em> argument specifies the path to the source package to be installed on the remote device in the advent of a version mismatch. The <em>src</em> argument can be either a localized path or a full path to the package file to install.</div></br>
    <div style="font-size: small;">aliases: package<div>        </td></tr>
                <tr><td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The <em>version</em> argument can be used to explicitly specify the version of the package that should be installed on the remote device.  If the <em>version</em> argument is not specified, then the version is extracts from the <em>src</em> filename.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # the required set of connection arguments have been purposely left off
    # the examples for brevity
    
    - name: install local package on remote device
      junos_package:
        src: junos-vsrx-12.1X46-D10.2-domestic.tgz
    
    - name: install local package on remote device without rebooting
      junos_package:
        src: junos-vsrx-12.1X46-D10.2-domestic.tgz
        reboot: no


Notes
-----

.. note::
    - This module requires the netconf system service be enabled on the remote device being managed



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
