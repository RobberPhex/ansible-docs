.. _bower:


bower - Manage bower packages with bower
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage bower packages with bower




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
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of a bower package to install</div></td></tr>
            <tr>
    <td>offline<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Install packages from local cache, if the packages were installed before</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The base path where to install the bower packages</div></td></tr>
            <tr>
    <td>production<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Install with --production flag</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td><div>The state of the bower package</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The version to be installed</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    description: Install "bootstrap" bower package.
    - bower: name=bootstrap
    
    description: Install "bootstrap" bower package on version 3.1.1.
    - bower: name=bootstrap version=3.1.1
    
    description: Remove the "bootstrap" bower package.
    - bower: name=bootstrap state=absent
    
    description: Install packages based on bower.json.
    - bower: path=/app/location
    
    description: Update packages based on bower.json to their latest version.
    - bower: path=/app/location state=latest




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

