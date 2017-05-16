.. _timezone:


timezone - Configure timezone setting
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module configures the timezone setting, both of the system clock and of the hardware clock. *Currently only Linux platform is supported.* It is recommended to restart ``crond`` after changing the timezone, otherwise the jobs may run at the wrong time. It uses the ``timedatectl`` command if available. Otherwise, it edits ``/etc/sysconfig/clock`` or ``/etc/timezone`` for the system clock, and uses the ``hwclock`` command for the hardware clock. If you want to set up the NTP, use :ref:`service <service>` module.




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
    <td>hwclock<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether the hardware clock is in UTC or in local timezone. Default is to keep current setting. Note that this option is recommended not to change and may fail to configure, especially on virtual environments such as AWS.</div></br>
        <div style="font-size: small;">aliases: rtc<div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the timezone for the system clock. Default is to keep current setting.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: set timezone to Asia/Tokyo
      timezone: name=Asia/Tokyo

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
        <td> diff </td>
        <td> The differences about the given arguments. </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> after </td>
        <td> The values after change </td>
        <td align=center>  </td>
        <td align=center> dict </td>
        <td align=center>  </td>
        </tr>
                <tr>
        <td> before </td>
        <td> The values before change </td>
        <td align=center>  </td>
        <td align=center> dict </td>
        <td align=center>  </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

