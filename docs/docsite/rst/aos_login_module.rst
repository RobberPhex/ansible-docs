.. _aos_login:


aos_login - Login to AOS server for session token
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Obtain the AOS server session token by providing the required username and password credentials.  Upon successful authentication, this module will return the session-token that is required by all subsequent AOS module usage. On success the module will automatically populate ansible facts with the variable *aos_session* This module is not idempotent and do not support check mode.


Requirements (on host that executes module)
-------------------------------------------

  * aos-pyez >= 0.6.0


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
                <tr><td>passwd<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>Password to use when connecting to the AOS server.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>8888</td>
        <td></td>
        <td><div>Port number to use when connecting to the AOS server.</div>        </td></tr>
                <tr><td>server<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Address of the AOS Server on which you want to open a connection.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>Login username to use when connecting to the AOS server.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: Create a session with the AOS-server
      aos_login:
        server: "{{ inventory_hostname }}"
        user: admin
        passwd: admin
    
    - name: Use the newly created session (register is not mandatory)
      aos_ip_pool:
        session: "{{ aos_session }}"
        name: my_ip_pool
        state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
