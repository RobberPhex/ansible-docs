.. _hostname:


hostname - Manage hostname
++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Set system's hostname, supports most OSs/Distributions, including those using systemd.
* Note, this module does *NOT* modify ``/etc/hosts``. You need to modify it yourself using other modules like template or replace.
* Windows, HP-UX and AIX are not currently supported


Requirements (on host that executes module)
-------------------------------------------

  * hostname


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
        <td><div>Name of the host</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - hostname:
        name: web01





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
