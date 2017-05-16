.. _cl_license:


cl_license - Install licenses fo Cumulus Linux
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2

DEPRECATED
----------

Deprecated in 2.3.

Synopsis
--------

* Installs a Cumulus Linux license. The module reports no change of status when a license is installed. For more details go the Cumulus Linux License Documentation at http://docs.cumulusnetwork.com and the Licensing KB Site at https://support.cumulusnetworks.com/hc/en-us/sections/200507688




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
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Force installation of a license. Typically not needed. It is recommended to manually run this command via the ansible command. A reload of switchd is not required. Running the force option in a playbook will break the idempotent state machine of the module and cause the switchd notification to kick in all the time, causing a disruption.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The full path to the license. Can be local path or HTTP URL.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example playbook using the cl_license module to manage licenses on Cumulus Linux
    
    - hosts: all
      tasks:
        - name: install license using http url
          cl_license:
            src: http://10.1.1.1/license.txt
          notify: restart switchd
    
        - name: Triggers switchd to be restarted right away, before play, or role
                is over. This is desired behaviour
          meta: flush_handlers
    
        - name: Configure interfaces
          template:
            src: interfaces.j2
            dest: /etc/network/interfaces
          notify: restart networking
    
      handlers:
       - name: restart switchd
         service:
          name: switchd
          state: restarted
       - name: restart networking
         service:
          name: networking
          state: reloaded
    
    # Force all switches to accept a new license. Typically not needed
    # ansible -m cl_license -a "src='http://10.1.1.1/new_lic' force=yes" -u root all

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
        <td> msg </td>
        <td> human-readable report of success or failure </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> interface bond0 config updated </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> whether the interface was changed </td>
        <td align=center> changed </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - To activate a license for the FIRST time, the switchd service must be restarted. This action is disruptive. The license renewal process occurs via the Cumulus Networks Customer Portal - http://customers.cumulusnetworks.com.
    - A non-EULA license is REQUIRED for automation. Manually install the license on a test switch, using the command "cl-license -i <license_file>" to confirm the license is a Non-EULA license. See EXAMPLES, for the proper way to issue this notify action.


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
