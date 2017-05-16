.. _hostname:


hostname - Manage hostname
++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Set system's hostname.
Currently implemented on Debian, Ubuntu, Fedora, RedHat, openSUSE, Linaro, ScientificLinux, Arch, CentOS, AMI.
Any distribution that uses systemd as their init system.
Note, this module does *NOT* modify /etc/hosts. You need to modify it yourself using other modules like template or replace.


Requirements
------------

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
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the host</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - hostname: name=web01




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

