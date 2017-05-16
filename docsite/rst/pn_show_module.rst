.. _pn_show:


pn_show - Run show commands on nvOS device.
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Execute show command in the nodes and returns the results read from the device.




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
        <td><div>Target switch(es) to run the cli on.</div></td></tr>
            <tr>
    <td>pn_cliusername<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Provide login username if user is not root.</div></td></tr>
            <tr>
    <td>pn_command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The <code>pn_command</code> takes a CLI show command as value.</div></td></tr>
            <tr>
    <td>pn_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify formatting options.</div></td></tr>
            <tr>
    <td>pn_parameters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Display output using a specific parameter. Use 'all' to display possible output. List of comma separated parameters.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: run the vlan-show command
      pn_show:
        pn_command: 'vlan-show'
        pn_parameters: id,scope,ports
        pn_options: 'layout vertical'
    
    - name: run the vlag-show command
      pn_show:
        pn_command: 'vlag-show'
        pn_parameters: 'id,name,cluster,mode'
        pn_options: 'no-show-headers'
    
    - name: run the cluster-show command
      pn_show:
        pn_command: 'cluster-show'

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
        <td> Indicates whether the CLI caused any change on the target. </td>
        <td align=center> always(False) </td>
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
        <td> The set of error responses from the show command. </td>
        <td align=center> on error </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The set of responses from the show command. </td>
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

