.. _accelerate:


accelerate - Enable accelerated mode on remote node
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

This modules launches an ephemeral *accelerate* daemon on the remote node which Ansible can use to communicate with nodes at high speed.
The daemon listens on a configurable port for a configurable amount of time.
Fireball mode is AES encrypted

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
    <td>ipv6</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The listener daemon on the remote host will bind to the ipv6 localhost socket if this parameter is set to true.</td>
    </tr>
            <tr>
    <td>minutes</td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td>The <em>accelerate</em> listener daemon is started on nodes and will stay around for this number of minutes before turning itself off.</td>
    </tr>
            <tr>
    <td>multi_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>When enabled, the daemon will open a local socket file which can be used by future daemon executions to upload a new key to the already running daemon, so that multiple users can connect using different keys. This access still requires an ssh connection as the uid for which the daemon is currently running. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>5099</td>
        <td><ul></ul></td>
        <td>TCP port for the socket connection</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>The number of seconds the socket will wait for data. If none is received when the timeout value is reached, the connection will be closed.</td>
    </tr>
        </table>


.. note:: Requires python-keyczar


Examples
--------

.. raw:: html

    <br/>


::

    # To use accelerate mode, simply add "accelerate: true" to your play. The initial
    # key exchange and starting up of the daemon will occur over SSH, but all commands and
    # subsequent actions will be conducted over the raw socket connection using AES encryption
    
    - hosts: devservers
      accelerate: true
      tasks:
          - command: /usr/bin/anything

.. note:: See the advanced playbooks chapter for more about using accelerated mode.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

