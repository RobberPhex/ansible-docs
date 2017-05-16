.. _ops_facts:


ops_facts - Collect device specific facts from OpenSwitch
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module collects additional device fact information from a remote device running OpenSwitch using either the CLI or REST interfaces.  It provides optional arguments for collecting fact information.




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
    <td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When enabled, this argument will collect the current running configuration from the remote device.  If the transport is <code>rest</code> then the collected configuration will be the full system configuration.</div></td></tr>
            <tr>
    <td>endpoints<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Accepts a list of endpoints to retrieve from the remote device using the REST API.  The endpoints should be valid endpoints availble on the device.  This argument is only valid when the transport is <code>rest</code>.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.  Note this argument does not affect the SSH argument.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>rest</em> transports.  Note this argument does not affect the SSH transport. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_PASSWORD will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when buiding the connection to the remote device.  This value applies to either <em>cli</em> or I().  The port value will default to the approriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).  Note this argument does not affect the SSH transport.</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convience method that allows all <span class='module'>openswitch</span> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transports. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_SSH_KEYFILE will be used instead.</div></td></tr>
            <tr>
    <td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>ssh</td>
        <td><ul><li>ssh</li><li>cli</li><li>rest</li></ul></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over ssh, cli or REST.</div></td></tr>
            <tr>
    <td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <em>transport</em> argument is configured as rest.  If the transport argument is not rest, this value is ignored</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the usename to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate either the CLI login or the eAPI authentication depending on which transport is used. Note this argument does not affect the SSH transport. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_USERNAME will be used instead.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: collect device facts
      ops_facts:
    
    - name: include the config
      ops_facts:
        config: yes
    
    - name: include a set of rest endpoints
      ops_facts:
        endpoints:
          - /system/interfaces/1
          - /system/interfaces/2

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
        <td> endpoints </td>
        <td> The JSON response from the URL endpoint </td>
        <td align=center> when endpoints argument is defined </td>
        <td align=center> list </td>
        <td align=center> [{'....': None}, {'....': None}] </td>
    </tr>
            <tr>
        <td> config </td>
        <td> The current system configuration </td>
        <td align=center> when enabled </td>
        <td align=center> string </td>
        <td align=center> .... </td>
    </tr>
            <tr>
        <td> hostname </td>
        <td> returns the configured hostname </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> ops01 </td>
    </tr>
            <tr>
        <td> version </td>
        <td> The current version of OpenSwitch </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 0.3.0 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: The use of the REST transport is still experimental until it is fully implemented


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

