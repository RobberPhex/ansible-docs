.. _digital_ocean_sshkey:


digital_ocean_sshkey - Create/delete an SSH key in DigitalOcean
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create/delete an SSH key.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * dopy


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
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>DigitalOcean api key.</div>        </td></tr>
                <tr><td>client_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>DigitalOcean manager id.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Numeric, the SSH key id you want to operate on.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>String, this is the name of an SSH key to create or destroy.</div>        </td></tr>
                <tr><td>ssh_pub_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The public SSH key you want to add to your account.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the target.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a SSH key is present
    # If a key matches this name, will return the ssh key id and changed = False
    # If no existing key matches this name, a new key is created, the ssh key id is returned and changed = False
    
    - digital_ocean_sshkey:
        state: present
        name: my_ssh_key
        ssh_pub_key: 'ssh-rsa AAAA...'
        client_id: XXX
        api_key: XXX
    


Notes
-----

.. note::
    - Two environment variables can be used, DO_CLIENT_ID and DO_API_KEY.
    - Version 1 of DigitalOcean API is used.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
