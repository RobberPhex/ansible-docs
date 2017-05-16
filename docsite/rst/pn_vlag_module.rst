.. _pn_vlag:


pn_vlag - CLI command to create/delete/modify vlag.
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Execute vlag-create/vlag-delete/vlag-modify command.
A virtual link aggregation group (VLAG) allows links that are physically connected to two different Pluribus Networks devices to appear as a single trunk to a third device. The third device can be a switch, server, or any Ethernet device. A VLAG can provide Layer 2 multipathing, which allows you to create redundancy by increasing bandwidth, enabling multiple parallel paths between nodes and loadbalancing traffic where alternative paths exist.




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
        <td><div>Target switch(es) to run this command on.</div></td></tr>
            <tr>
    <td>pn_cliusername<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Provide login username if user is not root.</div></td></tr>
            <tr>
    <td>pn_failover_action<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>move</li><li>ignore</li></ul></td>
        <td><div>Specify the failover action as move or ignore.</div></td></tr>
            <tr>
    <td>pn_lacp_fallback<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>bundle</li><li>individual</li></ul></td>
        <td><div>Specify the LACP fallback mode as bundles or individual.</div></td></tr>
            <tr>
    <td>pn_lacp_fallback_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the LACP fallback timeout in seconds. The range is between 30 and 60 seconds with a default value of 50 seconds.</div></td></tr>
            <tr>
    <td>pn_lacp_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>off</li><li>passive</li><li>active</li></ul></td>
        <td><div>Specify the LACP mode.</div></td></tr>
            <tr>
    <td>pn_lacp_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>slow</li><li>fast</li></ul></td>
        <td><div>Specify the LACP timeout as slow(30 seconds) or fast(4 seconds).</div></td></tr>
            <tr>
    <td>pn_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>active-active</li><li>active-standby</li></ul></td>
        <td><div>Specify the mode for the VLAG. Active-standby indicates one side is active and the other side is in standby mode. Active-active indicates that both sides of the vlag are up by default.</div></td></tr>
            <tr>
    <td>pn_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>pn_name</code> takes a valid name for vlag configuration.</div></td></tr>
            <tr>
    <td>pn_peer_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the peer VLAG port.</div><div>Required for vlag-create.</div></td></tr>
            <tr>
    <td>pn_peer_switch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the fabric-name of the peer switch.</div></td></tr>
            <tr>
    <td>pn_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the local VLAG port.</div><div>Required for vlag-create.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>update</li></ul></td>
        <td><div>State the action to perform. Use 'present' to create vlag, 'absent' to delete vlag and 'update' to modify vlag.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: create a VLAG
      pn_vlag:
        state: 'present'
        pn_name: spine-to-leaf
        pn_port: 'spine01-to-leaf'
        pn_peer_port: 'spine02-to-leaf'
        pn_peer_switch: spine02
        pn_mode: 'active-active'
    
    - name: delete VLAGs
      pn_vlag:
        state: 'absent'
        pn_name: spine-to-leaf

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
        <td> The set of error responses from the vlag command. </td>
        <td align=center> on error </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The set of responses from the vlag command. </td>
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

