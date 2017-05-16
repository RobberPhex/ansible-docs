.. _pn_vrouterlbif:


pn_vrouterlbif - CLI command to add/remove vrouter-loopback-interface.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Execute vrouter-loopback-interface-add, vrouter-loopback-interface-remove commands.
* Each fabric, cluster, standalone switch, or virtual network (VNET) can provide its tenants with a virtual router (vRouter) service that forwards traffic between networks and implements Layer 3 protocols.




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
                <tr><td>pn_index<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the interface index from 1 to 255.</div>        </td></tr>
                <tr><td>pn_interface_ip<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specify the IP address.</div>        </td></tr>
                <tr><td>pn_vrouter_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specify the name of the vRouter.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State the action to perform. Use 'present' to add vrouter loopback interface and 'absent' to remove vrouter loopback interface.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: add vrouter-loopback-interface
      pn_vrouterlbif:
        state: 'present'
        pn_vrouter_name: 'ansible-vrouter'
        pn_interface_ip: '104.104.104.1'
    
    - name: remove vrouter-loopback-interface
      pn_vrouterlbif:
        state: 'absent'
        pn_vrouter_name: 'ansible-vrouter'
        pn_interface_ip: '104.104.104.1'

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
        <td> The set of error responses from the vrouterlb command. </td>
        <td align=center> on error </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The set of responses from the vrouterlb command. </td>
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
