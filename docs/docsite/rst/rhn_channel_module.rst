.. _rhn_channel:


rhn_channel - Adds or removes Red Hat software channels
+++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Adds or removes Red Hat software channels


Requirements (on host that executes module)
-------------------------------------------

  * none


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
        <td><div>name of the software channel</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the user's password</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td></td>
        <td><div>whether the channel should be present or not</div>        </td></tr>
                <tr><td>sysname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>name of the system as it is known in RHN/Satellite</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The full url to the RHN/Satellite api</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>RHN/Satellite user</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - rhn_channel:
        name: rhel-x86_64-server-v2vwin-6
        sysname: server01
        url: https://rhn.redhat.com/rpc/api
        user: rhnuser
        password: guessme


Notes
-----

.. note::
    - this module fetches the system id from RHN.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
