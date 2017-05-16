.. _stacki_host:


stacki_host - Add or remove host to stacki front-end
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Use this module to add or remove hosts to a stacki front-end via API
* https://github.com/StackIQ/stacki




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
                <tr><td>force_install<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set value to True to force node into install state if it already exists in stacki.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the host to be added to Stacki.</div>        </td></tr>
                <tr><td>prim_intf<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the primary network interface.</div>        </td></tr>
                <tr><td>prim_intf_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IP Address for the primary network interface.</div>        </td></tr>
                <tr><td>prim_intf_mac<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>MAC Address for the primary PXE boot network interface.</div>        </td></tr>
                <tr><td>stacki_endpoint<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>URL for the Stacki API Endpoint.</div>        </td></tr>
                <tr><td>stacki_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for authenticating with Stacki API, but if not specified, the environment variable <code>stacki_password</code> is used instead.</div>        </td></tr>
                <tr><td>stacki_user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Username for authenticating with Stacki API, but if not specified, the environment variable <code>stacki_user</code> is used instead.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Add a host named test-1
      stacki_host:
        name: test-1
        stacki_user: usr
        stacki_password: pwd
        stacki_endpoint: url
        prim_intf_mac: mac_addr
        prim_intf_ip: x.x.x.x
        prim_intf: eth0
    
    - name: Remove a host named test-1
      stacki_host:
        name: test-1
        stacki_user: usr
        stacki_password: pwd
        stacki_endpoint: url
        state: absent

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
        <td> stdout_lines </td>
        <td> the value of stdout split into a list </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> [['...', '...'], ['...'], ['...']] </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> response to whether or not the api call completed successfully </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> the set of responses from the commands </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['...', '...'] </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
