.. _znode:


znode - Create, delete, retrieve, and update znodes using ZooKeeper.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------



Requirements
------------

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
            <tr>
    <td>hosts<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of ZooKeeper servers (format '[server]:[port]').</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path of the znode.</div></td></tr>
            <tr>
    <td>op<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>An operation to perform. Mutually exclusive with state.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The state to enforce. Mutually exclusive with op.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td><div>The amount of time to wait for a node to appear.</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The value assigned to the znode.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Creating or updating a znode with a given value
    - action: znode hosts=localhost:2181 name=/mypath value=myvalue state=present
    
    # Getting the value and stat structure for a znode
    - action: znode hosts=localhost:2181 name=/mypath op=get
    
    # Listing a particular znode's children
    - action: znode hosts=localhost:2181 name=/zookeeper op=list
    
    # Waiting 20 seconds for a znode to appear at path /mypath
    - action: znode hosts=localhost:2181 name=/mypath op=wait timeout=20
    
    # Deleting a znode at path /mypath
    - action: znode hosts=localhost:2181 name=/mypath state=absent




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

