.. _bower:


bower - Manage bower packages with bower
++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9

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
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of a bower package to install</td>
    </tr>
            <tr>
    <td>offline</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Install packages from local cache, if the packages were installed before</td>
    </tr>
            <tr>
    <td>path</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The base path where to install the bower packages</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td>The state of the bower package</td>
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

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

