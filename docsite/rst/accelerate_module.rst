.. _accelerate:


accelerate - Enable accelerated mode on remote node
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1

DEPRECATED
----------

in favor of SSH with ControlPersist

Synopsis
--------

This modules launches an ephemeral *accelerate* daemon on the remote node which Ansible can use to communicate with nodes at high speed.
The daemon listens on a configurable port for a configurable amount of time.
Fireball mode is AES encrypted


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.4
  * python-keyczar


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
    <td>ipv6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The listener daemon on the remote host will bind to the ipv6 localhost socket if this parameter is set to true.</div></td></tr>
            <tr>
    <td>minutes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>The <em>accelerate</em> listener daemon is started on nodes and will stay around for this number of minutes before turning itself off.</div></td></tr>
            <tr>
    <td>multi_key<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When enabled, the daemon will open a local socket file which can be used by future daemon executions to upload a new key to the already running daemon, so that multiple users can connect using different keys. This access still requires an ssh connection as the uid for which the daemon is currently running.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5099</td>
        <td><ul></ul></td>
        <td><div>TCP port for the socket connection</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td><div>The number of seconds the socket will wait for data. If none is received when the timeout value is reached, the connection will be closed.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # To use accelerate mode, simply add "accelerate: true" to your play. The initial
    # key exchange and starting up of the daemon will occur over SSH, but all commands and
    # subsequent actions will be conducted over the raw socket connection using AES encryption
    
    - hosts: devservers
      accelerate: true
      tasks:
          - command: /usr/bin/anything


Notes
-----

.. note:: See the advanced playbooks chapter for more about using accelerated mode.



For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

