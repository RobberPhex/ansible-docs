.. _cs_facts:


cs_facts - Gather facts on instances of Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module fetches data from the metadata API in CloudStack. The module must be called from within the instance itself.


Requirements
------------

  * yaml


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
    <td>filter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>cloudstack_service_offering</li><li>cloudstack_availability_zone</li><li>cloudstack_public_hostname</li><li>cloudstack_public_ipv4</li><li>cloudstack_local_hostname</li><li>cloudstack_local_ipv4</li><li>cloudstack_instance_id</li><li>cloudstack_user_data</li></ul></td>
        <td><div>Filter for a specific fact.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Gather all facts on instances
    - name: Gather cloudstack facts
      cs_facts:
    
    # Gather specific fact on instances
    - name: Gather cloudstack facts
      cs_facts: filter=cloudstack_instance_id

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
        <td> cloudstack_instance_id </td>
        <td> UUID of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ab4e80b0-3e7e-4936-bdc5-e334ba5b0139 </td>
    </tr>
            <tr>
        <td> cloudstack_public_ipv4 </td>
        <td> public IPv4 of the router. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 185.19.28.35 </td>
    </tr>
            <tr>
        <td> cloudstack_local_ipv4 </td>
        <td> local IPv4 of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 185.19.28.35 </td>
    </tr>
            <tr>
        <td> cloudstack_availability_zone </td>
        <td> zone the instance is deployed in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> cloudstack_local_hostname </td>
        <td> local hostname of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> VM-ab4e80b0-3e7e-4936-bdc5-e334ba5b0139 </td>
    </tr>
            <tr>
        <td> cloudstack_service_offering </td>
        <td> service offering of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Micro 512mb 1cpu </td>
    </tr>
            <tr>
        <td> cloudstack_public_hostname </td>
        <td> public IPv4 of the router. Same as C(cloudstack_public_ipv4). </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> VM-ab4e80b0-3e7e-4936-bdc5-e334ba5b0139 </td>
    </tr>
            <tr>
        <td> cloudstack_user_data </td>
        <td> data of the instance provided by users. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'bla': 'foo'} </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

