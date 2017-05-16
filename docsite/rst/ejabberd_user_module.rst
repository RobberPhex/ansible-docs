.. _ejabberd_user:


ejabberd_user - Manages users for ejabberd servers
++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

This module provides user management for ejabberd servers

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
    <td>host</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the ejabberd host associated with this username</td>
    </tr>
            <tr>
    <td>logging</td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li><li>yes</li><li>no</li></ul></td>
        <td>enables or disables the local syslog facility for this module</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the password to assign to the username</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>describe the desired state of the user to be managed</td>
    </tr>
            <tr>
    <td>username</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the name of the user to manage</td>
    </tr>
        </table>


.. note:: Requires ejabberd with mod_admin_extra


Examples
--------

.. raw:: html

    <br/>


::

    Example playbook entries using the ejabberd_user module to manage users state.
    
        tasks:
    
        - name: create a user if it does not exists
          action: ejabberd_user username=test host=server password=password
    
        - name: delete a user if it exists
          action: ejabberd_user username=test host=server state=absent

.. note:: Password parameter is required for state == present only
.. note:: Passwords must be stored in clear text for this release
.. note:: The ejabberd configuration file must include mod_admin_extra as a module.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

