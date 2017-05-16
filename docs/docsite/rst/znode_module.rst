.. _znode:


znode - Create, delete, retrieve, and update znodes using ZooKeeper
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, delete, retrieve, and update znodes using ZooKeeper.


Requirements (on host that executes module)
-------------------------------------------

  * kazoo >= 2.1
  * python >= 2.6


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
                <tr><td>hosts<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A list of ZooKeeper servers (format '[server]:[port]').</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The path of the znode.</div>        </td></tr>
                <tr><td>op<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>An operation to perform. Mutually exclusive with state.</div>        </td></tr>
                <tr><td>recursive<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Recursively delete node and all its children.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The state to enforce. Mutually exclusive with op.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>The amount of time to wait for a node to appear.</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The value assigned to the znode.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Creating or updating a znode with a given value
    - znode:
        hosts: 'localhost:2181'
        name: /mypath
        value: myvalue
        state: present
    
    # Getting the value and stat structure for a znode
    - znode:
        hosts: 'localhost:2181'
        name: /mypath
        op: get
    
    # Listing a particular znode's children
    - znode:
        hosts: 'localhost:2181'
        name: /zookeeper
        op: list
    
    # Waiting 20 seconds for a znode to appear at path /mypath
    - znode:
        hosts: 'localhost:2181'
        name: /mypath
        op: wait
        timeout: 20
    
    # Deleting a znode at path /mypath
    - znode:
        hosts: 'localhost:2181'
        name: /mypath
        state: absent
    
    # Creating or updating a znode with a given value on a remote Zookeeper
    - znode:
        hosts: 'my-zookeeper-node:2181'
        name: /mypath
        value: myvalue
        state: present
      delegate_to: 127.0.0.1





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
