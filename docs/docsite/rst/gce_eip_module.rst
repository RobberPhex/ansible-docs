.. _gce_eip:


gce_eip - Create or Destroy Global or Regional External IP addresses.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create (reserve) or Destroy (release) Regional or Global IP Addresses. See https://cloud.google.com/compute/docs/configure-instance-ip-addresses#reserve_new_static for more on reserving static addresses.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * apache-libcloud >= 0.19.0


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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of Address.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Region to create the address in. Set to 'global' to create a global address.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The state the address should be in. <code>present</code> or <code>absent</code> are the only valid options.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a Global external IP address
    gce_eip:
      service_account_email: "{{ service_account_email }}"
      credentials_file: "{{ credentials_file }}"
      project_id: "{{ project_id }}"
      name: my-global-ip
      region: global
      state: present
    
    # Create a Regional external IP address
    gce_eip:
      service_account_email: "{{ service_account_email }}"
      credentials_file: "{{ credentials_file }}"
      project_id: "{{ project_id }}"
      name: my-global-ip
      region: us-east1
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
        <td> region </td>
        <td> Which region an address belongs. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> global </td>
    </tr>
            <tr>
        <td> name </td>
        <td> name of the address being operated on </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> my-address </td>
    </tr>
            <tr>
        <td> address </td>
        <td> IP address being operated on </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 35.186.222.233 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Global addresses can only be used with Global Forwarding Rules.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
