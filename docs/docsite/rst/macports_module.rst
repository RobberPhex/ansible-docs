.. _macports:


macports - Package manager for MacPorts
+++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages MacPorts packages




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
        <td><div>name of package to install/remove</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>active</li><li>inactive</li></ul></td>
        <td><div>state of the package</div>        </td></tr>
                <tr><td>update_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>update the package db first</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - macports:
        name: foo
        state: present
    
    - macports:
        name: foo
        state: present
        update_cache: yes
    
    - macports:
        name: foo
        state: absent
    
    - macports:
        name: foo
        state: active
    
    - macports:
        name: foo
        state: inactive





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
