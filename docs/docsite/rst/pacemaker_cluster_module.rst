.. _pacemaker_cluster:


pacemaker_cluster - Manage a pacemaker cluster
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module can manage a pacemaker cluster and nodes from Ansible using the pacemaker cli.


Requirements (on host that executes module)
-------------------------------------------

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
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Force the change of the cluster state</div>        </td></tr>
                <tr><td>node<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Specify which node of the cluster you want to manage. None == the cluster status itself, 'all' == check the status of all nodes.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>online</li><li>offline</li><li>restart</li><li>cleanup</li></ul></td>
        <td><div>Indicate desired state of the cluster</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>Timeout when the module should considered that the action has failed</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    - name: Set cluster Online
      hosts: localhost
      gather_facts: no
      tasks:
        - name: get cluster state
          pacemaker_cluster: state=online

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> out </td>
        <td> The output of the current state of the cluster. It return a list of the nodes state. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> out: [["  overcloud-controller-0", " Online"]]} </td>
    </tr>
            <tr>
        <td> change </td>
        <td> True if the cluster state has changed </td>
        <td align=center>  </td>
        <td align=center> bool </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> rc </td>
        <td> exit code of the module </td>
        <td align=center>  </td>
        <td align=center> bool </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
