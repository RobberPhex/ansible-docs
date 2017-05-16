.. _pn_vlan:


pn_vlan - CLI command to create/delete a VLAN.
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Execute vlan-create or vlan-delete command.
* VLANs are used to isolate network traffic at Layer 2.The VLAN identifiers 0 and 4095 are reserved and cannot be used per the IEEE 802.1Q standard. The range of configurable VLAN identifiers is 2 through 4092.




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
                <tr><td>pn_clipassword<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Provide login password if user is not root.</div>        </td></tr>
                <tr><td>pn_cliswitch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Target switch(es) to run the cli on.</div>        </td></tr>
                <tr><td>pn_cliusername<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Provide login username if user is not root.</div>        </td></tr>
                <tr><td>pn_description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a description for the VLAN.</div>        </td></tr>
                <tr><td>pn_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the switch network data port number, list of ports, or range of ports. Port numbers must ne in the range of 1 to 64.</div>        </td></tr>
                <tr><td>pn_scope<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>fabric</li><li>local</li></ul></td>
        <td><div>Specify a scope for the VLAN.</div><div>Required for vlan-create.</div>        </td></tr>
                <tr><td>pn_stats<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if you want to collect statistics for a VLAN. Statistic collection is enabled by default.</div>        </td></tr>
                <tr><td>pn_untagged_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the ports that should have untagged packets mapped to the VLAN. Untagged packets are packets that do not contain IEEE 802.1Q VLAN tags.</div>        </td></tr>
                <tr><td>pn_vlanid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specify a VLAN identifier for the VLAN. This is a value between 2 and 4092.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State the action to perform. Use 'present' to create vlan and 'absent' to delete vlan.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: create a VLAN
      pn_vlan:
        state: 'present'
        pn_vlanid: 1854
        pn_scope: fabric
    
    - name: delete VLANs
      pn_vlan:
        state: 'absent'
        pn_vlanid: 1854

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
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stderr </td>
        <td> The set of error responses from the vlan command. </td>
        <td align=center> on error </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The set of responses from the vlan command. </td>
        <td align=center> always </td>
        <td align=center> list </td>
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
