.. _pingdom:


pingdom - Pause/unpause Pingdom alerts
++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module will let you pause/unpause Pingdom alerts


Requirements (on host that executes module)
-------------------------------------------

  * This pingdom python library: https://github.com/mbabineau/pingdom-python


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
                <tr><td>checkid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Pingdom ID of the check.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Pingdom API key.</div>        </td></tr>
                <tr><td>passwd<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Pingdom user password.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>running</li><li>paused</li></ul></td>
        <td><div>Define whether or not the check should be running or paused.</div>        </td></tr>
                <tr><td>uid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Pingdom user ID.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Pause the check with the ID of 12345.
    - pingdom:
        uid: example@example.com
        passwd: password123
        key: apipassword123
        checkid: 12345
        state: paused
    
    # Unpause the check with the ID of 12345.
    - pingdom:
        uid: example@example.com
        passwd: password123
        key: apipassword123
        checkid: 12345
        state: running


Notes
-----

.. note::
    - This module does not yet have support to add/remove checks.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
