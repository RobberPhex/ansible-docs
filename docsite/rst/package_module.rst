.. _package:


package - Generic OS package manager
++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Installs, upgrade and removes packages using the underlying OS package manager.


Requirements (on host that executes module)
-------------------------------------------

  * Whatever is required for the package plugins specific for each system.


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
        <td><div>Package name, or package specifier with version, like <code>name-1.0</code>.</div><div>Be aware that packages are not always named the same and this module will not 'translate' them per distro.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether to install (<code>present</code>, <code>latest</code>), or remove (<code>absent</code>) a package.</div></td></tr>
            <tr>
    <td>use<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>auto</td>
        <td><ul></ul></td>
        <td><div>The required package manager module to use (yum, apt, etc). The default 'auto' will use existing facts or try to autodetect it.</div><div>You should only use this field if the automatic selection is not working for some reason.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: install the latest version of ntpdate
      package: name=ntpdate state=latest
    
    # This uses a variable as this changes per distribution.
    - name: remove the apache package
      package: name={{apache}} state=absent


Notes
-----

.. note:: This module actually calls the pertinent package modules for each system (apt, yum, etc).


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

