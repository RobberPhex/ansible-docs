.. _pn_ospfarea:


pn_ospfarea - CLI command to add/remove ospf area to/from a vrouter.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Execute vrouter-ospf-add, vrouter-ospf-remove command.
This command adds/removes Open Shortest Path First(OSPF) area to/from a virtual router(vRouter) service.




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
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Login password.</div></td></tr>
            <tr>
    <td>pn_cliswitch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Target switch(es) to run the CLI on.</div></td></tr>
            <tr>
    <td>pn_cliusername<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Login username.</div></td></tr>
            <tr>
    <td>pn_ospf_area<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the OSPF area number.</div></td></tr>
            <tr>
    <td>pn_prefix_listin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>OSPF prefix list for filtering incoming packets.</div></td></tr>
            <tr>
    <td>pn_prefix_listout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>OSPF prefix list for filtering outgoing packets.</div></td></tr>
            <tr>
    <td>pn_quiet<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Enable/disable system information.</div></td></tr>
            <tr>
    <td>pn_stub_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>none</li><li>stub</li><li>stub-no-summary</li><li>nssa</li><li>nssa-no-summary</li></ul></td>
        <td><div>Specify the OSPF stub type.</div></td></tr>
            <tr>
    <td>pn_vrouter_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the name of the vRouter.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>update</li></ul></td>
        <td><div>State the action to perform. Use 'present' to add ospf-area, 'absent' to remove ospf-area and 'update' to modify ospf-area.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: "Add OSPF area to vrouter"
      pn_ospfarea:
        state: present
        pn_cliusername: admin
        pn_clipassword: admin
        pn_ospf_area: 1.0.0.0
        pn_stub_type: stub
    
    - name: "Remove OSPF from vrouter"
      pn_ospf:
        state: absent
        pn_cliusername: admin
        pn_clipassword: admin
        pn_vrouter_name: name-string
        pn_ospf_area: 1.0.0.0

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
        <td> The set of error responses from the ospf command. </td>
        <td align=center> on error </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The set of responses from the ospf command. </td>
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

