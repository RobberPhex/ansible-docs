.. _gem:


gem - Manage Ruby gems
++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

Manage installation and uninstallation of Ruby gems.

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
        <td>Override the path to the gem executable (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>gem_source</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The path to a local gem used as installation source.</td>
    </tr>
            <tr>
    <td>include_dependencies</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether to include dependencies or not.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the gem to be managed.</td>
    </tr>
            <tr>
    <td>pre_release</td>
    <td>no</td>
    <td>no</td>
        <td><ul></ul></td>
        <td>Allow installation of pre-release versions of the gem. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>repository</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The repository from which the gem will be installed</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td>The desired state of the gem. <code>latest</code> ensures that the latest version is installed.</td>
    </tr>
            <tr>
    <td>user_install</td>
    <td>no</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td>Install gem in user's local gems cache or for all users (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>version</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Version of the gem to be installed/removed.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Installs version 1.0 of vagrant.
    - gem: name=vagrant version=1.0 state=present
    
    # Installs latest available version of rake.
    - gem: name=rake state=latest
    
    # Installs rake version 1.0 from a local gem on disk.
    - gem: name=rake gem_source=/path/to/gems/rake-1.0.gem state=present



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

