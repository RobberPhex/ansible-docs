.. _npm:


npm - Manage node.js packages with npm
++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage node.js packages with Node Package Manager (npm)




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
                <tr><td>executable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The executable location for npm.</div><div>This is useful if you are using a version manager, such as nvm</div>        </td></tr>
                <tr><td>global<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Install the node.js library globally</div>        </td></tr>
                <tr><td>ignore_scripts<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Use the --ignore-scripts flag when installing.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of a node.js library to install</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The base path where to install the node.js libraries</div>        </td></tr>
                <tr><td>production<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Install dependencies in production mode, excluding devDependencies</div>        </td></tr>
                <tr><td>registry<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The registry to install modules from.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td><div>The state of the node.js library</div>        </td></tr>
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

    - name: Install "coffee-script" node.js package.
      npm:
        name: coffee-script
        path: /app/location
    
    - name: Install "coffee-script" node.js package on version 1.6.1.
      npm:
        name: coffee-script
        version: '1.6.1'
        path: /app/location
    
    - name: Install "coffee-script" node.js package globally.
      npm:
        name: coffee-script
        global: yes
    
    - name: Remove the globally package "coffee-script".
      npm:
        name: coffee-script
        global: yes
        state: absent
    
    - name: Install "coffee-script" node.js package from custom registry.
      npm:
        name: coffee-script
        registry: 'http://registry.mysite.com'
    
    - name: Install packages based on package.json.
      npm:
        path: /app/location
    
    - name: Update packages based on package.json to their latest version.
      npm:
        path: /app/location
        state: latest
    
    - name: Install packages based on package.json using the npm installed with nvm v0.10.1.
      npm:
        path: /app/location
        executable: /opt/nvm/v0.10.1/bin/npm
        state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
