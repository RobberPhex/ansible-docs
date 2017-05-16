.. _atomic_host:


atomic_host - Manage the atomic host platform
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage the atomic host platform
* Rebooting of Atomic host platform should be done outside this module


Requirements (on host that executes module)
-------------------------------------------

  * atomic
  * python >= 2.6


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
                <tr><td>revision<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>latest</td>
        <td></td>
        <td><div>The version number of the atomic host to be deployed. Providing <code>latest</code> will upgrade to the latest available version.</div></br>
    <div style="font-size: small;">aliases: version<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # Upgrade the atomic host platform to the latest version (atomic host upgrade)
    - atomic_host:
        revision: latest
    
    # Deploy a specific revision as the atomic host (atomic host deploy 23.130)
    - atomic_host:
        revision: 23.130

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
        <td> msg </td>
        <td> The command standard output </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> Already on latest </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Host should be an atomic platform (verified by existence of '/run/ostree-booted' file)



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
