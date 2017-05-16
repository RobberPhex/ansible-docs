.. _bower:


bower - Manage bower packages with bower
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage bower packages with bower




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
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of a bower package to install</div>        </td></tr>
                <tr><td>offline<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Install packages from local cache, if the packages were installed before</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The base path where to install the bower packages</div>        </td></tr>
                <tr><td>production<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Install with --production flag</div>        </td></tr>
                <tr><td>relative_execpath<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Relative path to bower executable from install path</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td><div>The state of the bower package</div>        </td></tr>
                <tr><td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The version to be installed</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Install "bootstrap" bower package.
      bower:
        name: bootstrap
    
    - name: Install "bootstrap" bower package on version 3.1.1.
      bower:
        name: bootstrap
        version: '3.1.1'
    
    - name: Remove the "bootstrap" bower package.
      bower:
        name: bootstrap
        state: absent
    
    - name: Install packages based on bower.json.
      bower:
        path: /app/location
    
    - name: Update packages based on bower.json to their latest version.
      bower:
        path: /app/location
        state: latest
    
    # install bower locally and run from there
    - npm:
        path: /app/location
        name: bower
        global: no
    - bower:
        path: /app/location
        relative_execpath: node_modules/.bin





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
