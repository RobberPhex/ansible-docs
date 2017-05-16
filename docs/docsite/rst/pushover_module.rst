.. _pushover:


pushover - Send notifications via https://pushover.net
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Send notifications via pushover, to subscriber list of devices, and email addresses. Requires pushover app on devices.




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
                <tr><td>app_token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Pushover issued token identifying your pushover app.</div>        </td></tr>
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>What message you wish to send.</div>        </td></tr>
                <tr><td>pri<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Message priority (see <a href='https://pushover.net'>https://pushover.net</a> for details.)</div>        </td></tr>
                <tr><td>user_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Pushover issued authentication key for your user.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - pushover:
        msg: '{{ inventory_hostname }} has exploded in flames, It is now time to panic'
        app_token: wxfdksl
        user_key: baa5fe97f2c5ab3ca8f0bb59
      delegate_to: localhost


Notes
-----

.. note::
    - You will require a pushover.net account to use this module. But no account is required to receive messages.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
