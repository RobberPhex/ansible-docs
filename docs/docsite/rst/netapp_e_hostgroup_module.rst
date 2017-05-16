.. _netapp_e_hostgroup:


netapp_e_hostgroup - Manage NetApp Storage Array Host Groups
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update or destroy host groups on a NetApp E-Series storage array.




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
                <tr><td>api_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password to authenticate with the SANtricity WebServices Proxy or embedded REST API.</div>        </td></tr>
                <tr><td>api_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The url to the SANtricity WebServices Proxy or embedded REST API.</div>        </td></tr>
                <tr><td>api_username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username to authenticate with the SANtricity WebServices Proxy or embedded REST API.</div>        </td></tr>
                <tr><td>hosts:<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a list of host names/labels to add to the group</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The id number of the host group to manage. Either this or <code>name</code> must be supplied.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the host group to manage. Either this or <code>id_num</code> must be supplied.</div>        </td></tr>
                <tr><td>new_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>specify this when you need to update the name of a host group</div>        </td></tr>
                <tr><td>ssid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The ID of the array to manage (as configured on the web services proxy).</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified host group should exist or not.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Should https certificates be validated?</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

        - name: Configure Hostgroup
          netapp_e_hostgroup:
            ssid: "{{ ssid }}"
            api_url: "{{ netapp_api_url }}"
            api_username: "{{ netapp_api_username }}"
            api_password: "{{ netapp_api_password }}"
            validate_certs: "{{ netapp_api_validate_certs }}"
            state: present

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
        <td> isSAControlled </td>
        <td> If true, indicates that I/O accesses from this cluster are subject to the storage array's default LUN-to-volume mappings. If false, indicates that I/O accesses from the cluster are subject to cluster-specific LUN-to-volume mappings. </td>
        <td align=center> always except when state is absent </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> name </td>
        <td> same as label </td>
        <td align=center> always except when state is absent </td>
        <td align=center> string </td>
        <td align=center> MyHostGroup </td>
    </tr>
            <tr>
        <td> confirmLUNMappingCreation </td>
        <td> If true, indicates that creation of LUN-to-volume mappings should require careful confirmation from the end-user, since such a mapping will alter the volume access rights of other clusters, in addition to this one. </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> label </td>
        <td> The user-assigned, descriptive label string for the cluster. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> MyHostGroup </td>
    </tr>
            <tr>
        <td> clusterRef </td>
        <td> The unique identification value for this object. Other objects may use this reference value to refer to the cluster. </td>
        <td align=center> always except when state is absent </td>
        <td align=center> string </td>
        <td align=center> 3233343536373839303132333100000000000000 </td>
    </tr>
            <tr>
        <td> hosts </td>
        <td> A list of the hosts that are part of the host group after all operations. </td>
        <td align=center> always except when state is absent </td>
        <td align=center> list </td>
        <td align=center> ['HostA', 'HostB'] </td>
    </tr>
            <tr>
        <td> id </td>
        <td> The id number of the hostgroup </td>
        <td align=center> always except when state is absent </td>
        <td align=center> string </td>
        <td align=center> 3233343536373839303132333100000000000000 </td>
    </tr>
            <tr>
        <td> protectionInformationCapableAccessMethod </td>
        <td> This field is true if the host has a PI capable access method. </td>
        <td align=center> always except when state is absent </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
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
