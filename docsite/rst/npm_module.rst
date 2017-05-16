.. _npm:


npm - Manage node.js packages with npm
++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Manage node.js packages with Node Package Manager (npm)

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
    <td>executable</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The executable location for npm.This is useful if you are using a version manager, such as nvm</td>
    </tr>
            <tr>
    <td>global</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Install the node.js library globally</td>
    </tr>
            <tr>
    <td>ignore_scripts</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Use the --ignore-scripts flag when installing. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of a node.js library to install</td>
    </tr>
            <tr>
    <td>path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The base path where to install the node.js libraries</td>
    </tr>
            <tr>
    <td>production</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Install dependencies in production mode, excluding devDependencies</td>
    </tr>
            <tr>
    <td>registry</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The registry to install modules from. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td>The state of the node.js library</td>
    </tr>
            <tr>
    <td>version</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The version to be installed</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    description: Install "coffee-script" node.js package.
    - npm: name=coffee-script path=/app/location
    
    description: Install "coffee-script" node.js package on version 1.6.1.
    - npm: name=coffee-script version=1.6.1 path=/app/location
    
    description: Install "coffee-script" node.js package globally.
    - npm: name=coffee-script global=yes
    
    description: Remove the globally package "coffee-script".
    - npm: name=coffee-script global=yes state=absent
    
    description: Install "coffee-script" node.js package from custom registry.
    - npm: name=coffee-script registry=http://registry.mysite.com
    
    description: Install packages based on package.json.
    - npm: path=/app/location
    
    description: Update packages based on package.json to their latest version.
    - npm: path=/app/location state=latest
    
    description: Install packages based on package.json using the npm installed with nvm v0.10.1.
    - npm: path=/app/location executable=/opt/nvm/v0.10.1/bin/npm state=present



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

