.. _supervisorctl:


supervisorctl - Manage the state of a program or group of programs running via supervisord
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Manage the state of a program or group of programs running via supervisord

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
    <td>config</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The supervisor configuration file path (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the supervisord program or group to manage.The name will be taken as group name when it ends with a colon <em>:</em>Group support is only available in Ansible version 1.6 or later.</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>password to use for authentication (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>server_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>URL on which supervisord server is listening (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>started</li><li>stopped</li><li>restarted</li></ul></td>
        <td>The desired state of program/group.</td>
    </tr>
            <tr>
    <td>supervisorctl_path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to supervisorctl executable (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>username to use for authentication (added in Ansible 1.3)</td>
    </tr>
        </table>


.. note:: Requires supervisorctl


Examples
--------

.. raw:: html

    <br/>


::

    # Manage the state of program to be in 'started' state.
    - supervisorctl: name=my_app state=started
    
    # Manage the state of program group to be in 'started' state.
    - supervisorctl: name='my_apps:' state=started
    
    # Restart my_app, reading supervisorctl configuration from a specified file.
    - supervisorctl: name=my_app state=restarted config=/var/opt/my_project/supervisord.conf
    
    # Restart my_app, connecting to supervisord with credentials and server URL.
    - supervisorctl: name=my_app state=restarted username=test password=testpass server_url=http://localhost:9001

.. note:: When ``state`` = *present*, the module will call ``supervisorctl reread`` then ``supervisorctl add`` if the program/group does not exist.
.. note:: When ``state`` = *restarted*, the module will call ``supervisorctl update`` then call ``supervisorctl restart``.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

