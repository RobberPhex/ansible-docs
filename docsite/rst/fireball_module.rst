.. _fireball:


fireball - Enable fireball mode on remote node
++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


This modules launches an ephemeral *fireball* ZeroMQ message bus daemon on the remote node which Ansible can use to communicate with nodes at high speed.
The daemon listens on a configurable port for a configurable amount of time.
Starting a new fireball as a given user terminates any existing user fireballs.
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
    <td>minutes</td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td>The <em>fireball</em> listener daemon is started on nodes and will stay around for this number of minutes before turning itself off.</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>5099</td>
        <td><ul></ul></td>
        <td>TCP port for ZeroMQ</td>
    </tr>
        </table>


.. note:: Requires zmq


.. note:: Requires keyczar


Examples
--------

.. raw:: html

    <br/>


::

    # This example playbook has two plays: the first launches 'fireball' mode on all hosts via SSH, and 
    # the second actually starts using it for subsequent management over the fireball connection
    
    - hosts: devservers
      gather_facts: false
      connection: ssh
      sudo: yes
      tasks:
          - action: fireball
    
    - hosts: devservers
      connection: fireball
      tasks:
          - command: /usr/bin/anything

.. note:: See the advanced playbooks chapter for more about using fireball mode.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

