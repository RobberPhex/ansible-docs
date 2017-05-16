.. _pn_cluster:


pn_cluster - CLI command to create/delete a cluster.
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Execute cluster-create or cluster-delete command.
A cluster allows two switches to cooperate in high-availability (HA) deployments. The nodes that form the cluster must be members of the same fabric. Clusters are typically used in conjunction with a virtual link aggregation group (VLAG) that allows links physically connected to two separate switches appear as a single trunk to a third device. The third device can be a switch,server, or any Ethernet device.




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
    <td>pn_clipassword<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Provide login password if user is not root.</div></td></tr>
            <tr>
    <td>pn_cliswitch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Target switch to run the cli on.</div></td></tr>
            <tr>
    <td>pn_cliusername<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Provide login username if user is not root.</div></td></tr>
            <tr>
    <td>pn_cluster_node1<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the name of the first switch in the cluster.</div><div>Required for 'cluster-create'.</div></td></tr>
            <tr>
    <td>pn_cluster_node2<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the name of the second switch in the cluster.</div><div>Required for 'cluster-create'.</div></td></tr>
            <tr>
    <td>pn_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the name of the cluster.</div></td></tr>
            <tr>
    <td>pn_validate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>validate</li><li>no-validate</li></ul></td>
        <td><div>Validate the inter-switch links and state of switches in the cluster.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Specify action to perform. Use 'present' to create cluster and 'absent' to delete cluster.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: create spine cluster
      pn_cluster:
        state: 'present'
        pn_name: 'spine-cluster'
        pn_cluster_node1: 'spine01'
        pn_cluster_node2: 'spine02'
        pn_validate: validate
        pn_quiet: True
    
    - name: delete spine cluster
      pn_cluster:
        state: 'absent'
        pn_name: 'spine-cluster'
        pn_quiet: True

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
        <td> changed </td>
        <td> Indicates whether the CLI caused changes on the target. </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> command </td>
        <td> The CLI command run on the target node(s). </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stderr </td>
        <td> The set of error responses from the cluster command. </td>
        <td align=center> on error </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The set of responses from the cluster command. </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

