.. _consul_session:


consul_session - manipulate consul sessions
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* allows the addition, modification and deletion of sessions in a consul cluster. These sessions can then be used in conjunction with key value pairs to implement distributed locks. In depth documentation for working with sessions can be found here http://www.consul.io/docs/internals/sessions.html


Requirements (on host that executes module)
-------------------------------------------

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
                <tr><td>behavior<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>release</td>
        <td></td>
        <td><div>the optional behavior that can be attached to the session when it is created. This can be set to either ‘release’ or ‘delete’. This controls the behavior when a session is invalidated.</div>        </td></tr>
                <tr><td>checks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>a list of checks that will be used to verify the session health. If all the checks fail, the session will be invalidated and any locks associated with the session will be release and can be acquired once the associated lock delay has expired.</div>        </td></tr>
                <tr><td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>name of the datacenter in which the session exists or should be created.</div>        </td></tr>
                <tr><td>delay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>15</td>
        <td></td>
        <td><div>the optional lock delay that can be attached to the session when it is created. Locks for invalidated sessions ar blocked from being acquired until this delay has expired. Durations are in seconds</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td></td>
        <td><div>host of the consul agent defaults to localhost</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>the name that should be associated with the session. This is opaque to Consul and not required.</div>        </td></tr>
                <tr><td>node<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>the name of the node that with which the session will be associated. by default this is the name of the agent.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>8500</td>
        <td></td>
        <td><div>the port on which the consul agent is running</div>        </td></tr>
                <tr><td>scheme<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>http</td>
        <td></td>
        <td><div>the protocol scheme on which the consul agent is running</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>info</li><li>node</li><li>list</li></ul></td>
        <td><div>whether the session should be present i.e. created if it doesn't exist, or absent, removed if present. If created, the ID for the session is returned in the output. If absent, the name or ID is required to remove the session. Info for a single session, all the sessions for a node or all available sessions can be retrieved by specifying info, node or list for the state; for node or info, the node name or session id is required as parameter.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>whether to verify the tls certificate of the consul agent</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: register basic session with consul
      consul_session:
        name: session1
    
    - name: register a session with an existing check
      consul_session:
        name: session_with_check
        checks:
          - existing_check_name
    
    - name: register a session with lock_delay
      consul_session:
        name: session_with_delay
        delay: 20s
    
    - name: retrieve info about session by id
      consul_session: id=session_id state=info
    
    - name: retrieve active sessions
      consul_session: state=list





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
