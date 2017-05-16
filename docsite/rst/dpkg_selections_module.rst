.. _dpkg_selections:


dpkg_selections - Dpkg package selection selections
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Change dpkg package selection state via --get-selections and --set-selections.




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
        <td><div>Name of the package</div></td></tr>
            <tr>
    <td>selection<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>install</li><li>hold</li><li>deinstall</li><li>purge</li></ul></td>
        <td><div>The selection state to set the package to.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Prevent python from being upgraded.
    - dpkg_selections: name=python selection=hold


Notes
-----

.. note:: This module won't cause any packages to be installed/removed/purged, use the ``apt`` module for that.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

