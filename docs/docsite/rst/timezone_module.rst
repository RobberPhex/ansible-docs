.. _timezone:


timezone - Configure timezone setting
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module configures the timezone setting, both of the system clock and of the hardware clock. If you want to set up the NTP, use :ref:`service <service>` module.
* It is recommended to restart ``crond`` after changing the timezone, otherwise the jobs may run at the wrong time.
* Several different tools are used depending on the OS/Distribution involved. For Linux it can use ``timedatectl``  or edit ``/etc/sysconfig/clock`` or ``/etc/timezone`` and``hwclock``. On SmartOS , ``sm-set-timezone``, for BSD, ``/etc/localtime`` is modified.
* As of version 2.3 support was added for SmartOS and BSDs.
* Windows, AIX and HPUX are not supported, please let us know if you find any other OS/distro in which this fails.




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
                <tr><td>hwclock<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether the hardware clock is in UTC or in local timezone. Default is to keep current setting. Note that this option is recommended not to change and may fail to configure, especially on virtual environments such as AWS. <b>At least one of name and hwclock are required.</b> <em>Only used on Linux.</em></div></br>
    <div style="font-size: small;">aliases: rtc<div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the timezone for the system clock. Default is to keep current setting. <b>At least one of name and hwclock are required.</b></div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: set timezone to Asia/Tokyo
      timezone:
        name: Asia/Tokyo

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

Notes
-----

.. note::
    - On SmartOS the ``sm-set-timezone`` utility (part of the smtools package) is required to set the zone timezone



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
