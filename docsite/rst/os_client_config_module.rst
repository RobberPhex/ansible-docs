.. _os_client_config:


os_client_config - Get OpenStack Client config
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Get *openstack* client config data from clouds.yaml or environment


Requirements (on host that executes module)
-------------------------------------------

  * os-client-config


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
    <td>clouds<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of clouds to limit the return list to. No value means return information on all configured clouds</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Get list of clouds that do not support security groups
    - os_client_config:
    - debug: var={{ item }}
      with_items: "{{ openstack.clouds|rejectattr('secgroup_source', 'none')|list() }}"
    
    # Get the information back just about the mordred cloud
    - os_client_config:
        clouds:
        - mordred


Notes
-----

.. note:: Facts are placed in the ``openstack.clouds`` variable.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

