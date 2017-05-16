.. _foreman:


foreman - Manage Foreman Resources
++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Allows the management of Foreman resources inside your Foreman server


Requirements (on host that executes module)
-------------------------------------------

  * nailgun >= 0.28.0
  * python >= 2.6
  * datetime


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
                <tr><td>entity<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The Foreman resource that the action will be performed on (e.g. organization, host)</div>        </td></tr>
                <tr><td>params<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Parameters associated to the entity resource to set or edit in dictionary format (e.g. name, description)</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for user accessing Foreman server</div>        </td></tr>
                <tr><td>server_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>URL of Foreman server</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Username on Foreman server</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: "Create CI Organization"
      local_action:
          module: foreman
          username: "admin"
          password: "admin"
          server_url: "https://fakeserver.com"
          entity: "organization"
          params:
            name: "My Cool New Organization"





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
