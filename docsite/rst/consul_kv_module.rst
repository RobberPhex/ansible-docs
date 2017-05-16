.. _consul_kv:


consul_kv - Manipulate entries in the key/value store of a consul cluster.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Allows the addition, modification and deletion of key/value entries in a consul cluster via the agent. The entire contents of the record, including the indices, flags and session are returned as 'value'.
If the key represents a prefix then Note that when a value is removed, the existing value if any is returned as part of the results.
See http://www.consul.io/docs/agent/http.html#kv for more details.


Requirements
------------

  * python >= 2.6
  * python-consul
  * requests


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
    <td>cas<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>used when acquiring a lock with a session. If the cas is 0, then Consul will only put the key if it does not already exist. If the cas value is non-zero, then the key is only set if the index matches the ModifyIndex of that key.</div></td></tr>
            <tr>
    <td>flags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>opaque integer value that can be passed when setting a value.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>host of the consul agent defaults to localhost</div></td></tr>
            <tr>
    <td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the key at which the value should be stored.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>8500</td>
        <td><ul></ul></td>
        <td><div>the port on which the consul agent is running</div></td></tr>
            <tr>
    <td>recurse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>if the key represents a prefix, each entry with the prefix can be retrieved by setting this to true.</div></td></tr>
            <tr>
    <td>session<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>the session that should be used to acquire or release a lock associated with a key/value pair</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>acquire</li><li>release</li></ul></td>
        <td><div>the action to take with the supplied key and value. If the state is 'present', the key contents will be set to the value supplied, 'changed' will be set to true only if the value was different to the current contents. The state 'absent' will remove the key/value pair, again 'changed' will be set to true only if the key actually existed prior to the removal. An attempt can be made to obtain or free the lock associated with a key/value pair with the states 'acquire' or 'release' respectively. a valid session must be supplied to make the attempt changed will be true if the attempt is successful, false otherwise.</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>the token key indentifying an ACL rule set that controls access to the key value pair</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the value should be associated with the given key, required if state is present</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
      - name: add or update the value associated with a key in the key/value store
        consul_kv:
          key: somekey
          value: somevalue
    
      - name: remove a key from the store
        consul_kv:
          key: somekey
          state: absent
    
      - name: add a node to an arbitrary group via consul inventory (see consul.ini)
        consul_kv:
          key: ansible/groups/dc1/somenode
          value: 'top_secret'




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

