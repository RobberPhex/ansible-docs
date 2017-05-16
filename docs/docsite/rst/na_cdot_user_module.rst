.. _na_cdot_user:


na_cdot_user - useradmin configuration and management
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create or destroy users.


Requirements (on host that executes module)
-------------------------------------------

  * A physical or virtual clustered Data ONTAP system. The modules were developed with Clustered Data ONTAP 8.3
  * Ansible 2.2
  * netapp-lib (2015.9.25). Install using 'pip install netapp-lib'


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
                <tr><td>application<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>console</li><li>http</li><li>ontapi</li><li>rsh</li><li>snmp</li><li>sp</li><li>ssh</li><li>telnet</li></ul></td>
        <td><div>Applications to grant access to.</div>        </td></tr>
                <tr><td>authentication_method<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>community</li><li>password</li><li>publickey</li><li>domain</li><li>nsswitch</li><li>usm</li></ul></td>
        <td><div>Authentication method for the application.</div><div>Not all authentication methods are valid for an application.</div><div>Valid authentication methods for each application are as denoted in <em>authentication_choices_description</em>.</div><div>password for console application</div><div>password, domain, nsswitch, cert for http application.</div><div>password, domain, nsswitch, cert for ontapi application.</div><div>community for snmp application (when creating SNMPv1 and SNMPv2 users).</div><div>usm and community for snmp application (when creating SNMPv3 users).</div><div>password for sp application.</div><div>password for rsh application.</div><div>password for telnet application.</div><div>password, publickey, domain, nsswitch for ssh application.</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the ONTAP instance.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the user to manage.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the specified user.</div>        </td></tr>
                <tr><td>role_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the role. Required when <code>state=present</code></div>        </td></tr>
                <tr><td>set_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Password for the user account.</div><div>It is ignored for creating snmp users, but is required for creating non-snmp users.</div><div>For an existing user, this value will be used as the new password.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified user should exist or not.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This can be a Cluster-scoped or SVM-scoped account, depending on whether a Cluster-level or SVM-level API is required. For more information, please read the documentation <a href='https://goo.gl/BRu78Z'>https://goo.gl/BRu78Z</a>.</div>        </td></tr>
                <tr><td>vserver<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the vserver to use.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
        - name: Create User
          na_cdot_user:
            state: present
            name: SampleUser
            application: ssh
            authentication_method: password
            set_password: apn1242183u1298u41
            role_name: vsadmin
            vserver: ansibleVServer
            hostname: "{{ netapp_hostname }}"
            username: "{{ netapp_username }}"
            password: "{{ netapp_password }}"
    


Notes
-----

.. note::
    - The modules prefixed with ``netapp\_cdot`` are built to support the ONTAP storage platform.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
