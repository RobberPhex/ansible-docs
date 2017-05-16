.. _pn_vrouter:


pn_vrouter - CLI command to create/delete/modify a vrouter.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Execute vrouter-create, vrouter-delete, vrouter-modify command.
* Each fabric, cluster, standalone switch, or virtual network (VNET) can provide its tenants with a virtual router (vRouter) service that forwards traffic between networks and implements Layer 3 protocols.
* ``vrouter-create`` creates a new vRouter service.
* ``vrouter-delete`` deletes a vRouter service.
* ``vrouter-modify`` modifies a vRouter service.




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
                <tr><td>pn_bgp_as<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the Autonomous System Number(ASN) if the vRouter runs Border Gateway Protocol(BGP).</div>        </td></tr>
                <tr><td>pn_bgp_max_paths<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the maximum number of paths for BGP. This is a number between 1 and 255 or 0 to unset.</div>        </td></tr>
                <tr><td>pn_bgp_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify other BGP options as a whitespaces separated string within single quotes ''.</div>        </td></tr>
                <tr><td>pn_bgp_redistribute<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>static</li><li>connected</li><li>rip</li><li>ospf</li></ul></td>
        <td><div>Specify how BGP routes are redistributed.</div>        </td></tr>
                <tr><td>pn_clipassword<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Provide login password if user is not root.</div>        </td></tr>
                <tr><td>pn_cliswitch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Target switch(es) to run the CLI on.</div>        </td></tr>
                <tr><td>pn_cliusername<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Provide login username if user is not root.</div>        </td></tr>
                <tr><td>pn_hw_vrrp_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the VRRP ID for a hardware vrouter.</div>        </td></tr>
                <tr><td>pn_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specify the name of the vRouter.</div>        </td></tr>
                <tr><td>pn_ospf_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify other OSPF options as a whitespaces separated string within single quotes ''.</div>        </td></tr>
                <tr><td>pn_ospf_redistribute<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>static</li><li>connected</li><li>bgp</li><li>rip</li></ul></td>
        <td><div>Specify how OSPF routes are redistributed.</div>        </td></tr>
                <tr><td>pn_rip_redistribute<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>static</li><li>connected</li><li>ospf</li><li>bgp</li></ul></td>
        <td><div>Specify how RIP routes are redistributed.</div>        </td></tr>
                <tr><td>pn_router_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the vRouter IP address.</div>        </td></tr>
                <tr><td>pn_router_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>hardware</li><li>software</li></ul></td>
        <td><div>Specify if the vRouter uses software or hardware.</div><div>Note that if you specify hardware as router type, you cannot assign IP addresses using DHCP. You must specify a static IP address.</div>        </td></tr>
                <tr><td>pn_service_state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li><li>disable</li></ul></td>
        <td><div>Specify to enable or disable vRouter service.</div>        </td></tr>
                <tr><td>pn_service_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>dedicated</li><li>shared</li></ul></td>
        <td><div>Specify if the vRouter is a dedicated or shared VNET service.</div>        </td></tr>
                <tr><td>pn_vnet<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the name of the VNET.</div><div>Required for vrouter-create.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>update</li></ul></td>
        <td><div>State the action to perform. Use 'present' to create vrouter, 'absent' to delete vrouter and 'update' to modify vrouter.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: create vrouter
      pn_vrouter:
        state: 'present'
        pn_name: 'ansible-vrouter'
        pn_vnet: 'ansible-fab-global'
        pn_router_id: 208.74.182.1
    
    - name: delete vrouter
      pn_vrouter:
        state: 'absent'
        pn_name: 'ansible-vrouter'

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
        <td> The set of error responses from the vrouter command. </td>
        <td align=center> on error </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The set of responses from the vrouter command. </td>
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
