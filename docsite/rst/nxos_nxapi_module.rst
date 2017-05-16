.. _nxos_nxapi:


nxos_nxapi - Manage NXAPI configuration on an NXOS device.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Use to enable or disable NXAPI access, set the port and state of http and https servers, and enable or disable the sandbox.
When enabling NXAPI access the default is to enable HTTP on port 80, enable HTTPS on port 443, and enable the web based UI sandbox. Use the options below to override the default configuration.




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
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>http<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Enable/disable HTTP server.</div></br>
        <div style="font-size: small;">aliases: enable_http<div></td></tr>
            <tr>
    <td>http_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>80</td>
        <td><ul></ul></td>
        <td><div>Port on which the HTTP server will listen.</div></td></tr>
            <tr>
    <td>https<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Enable/disable HTTPS server.</div></br>
        <div style="font-size: small;">aliases: enable_https<div></td></tr>
            <tr>
    <td>https_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>443</td>
        <td><ul></ul></td>
        <td><div>Port on which the HTTPS server will listen.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>nxapi</em> transports. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_PASSWORD will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when buiding the connection to the remote device.  This value applies to either <em>cli</em> or <em>nxapi</em>.  The port value will default to the approriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convience method that allows all <span class='module'>nxos</span> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>sandbox<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Enable/disable NXAPI web based UI for entering commands.</div></br>
        <div style="font-size: small;">aliases: enable_sandbox<div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_SSH_KEYFILE will be used instead.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>started</li><li>stopped</li></ul></td>
        <td><div>Set to started or stopped. A state of started will enable NXAPI access, and a state of stopped will disable or shutdown all NXAPI access.</div></td></tr>
            <tr>
    <td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>cli</td>
        <td><ul></ul></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over cli (ssh) or nxapi.</div></td></tr>
            <tr>
    <td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <em>transport</em> argument is configured as nxapi.  If the transport argument is not nxapi, this value is ignored</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the usename to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate either the CLI login or the nxapi authentication depending on which transport is used. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_USERNAME will be used instead.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

        - name: Enable NXAPI access with default configuration
          nxos_nxapi:
              provider: {{ provider }}
    
        - name: Enable NXAPI with no HTTP, HTTPS at port 9443 and sandbox disabled
          nxos_nxapi:
              enable_http: false
              https_port: 9443
              enable_sandbox: no
              provider: {{ provider }}
    
        - name: shutdown NXAPI access
          nxos_nxapi:
              state: stopped
              provider: {{ provider }}

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
        <td> commands </td>
        <td> ['Set of commands to be executed on remote device. If run in check mode, commands will not be executed.'] </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['nxapi feature', 'nxapi http port 8080'] </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> ['Indicates if commands were sent to the device.'] </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> _config </td>
        <td> ['Configuration found on the device prior ro any commands being executed.'] </td>
        <td align=center> always </td>
        <td align=center> object </td>
        <td align=center> {'...': None} </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

