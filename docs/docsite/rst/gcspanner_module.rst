.. _gcspanner:


gcspanner - Create and Delete Instances/Databases on Spanner.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create and Delete Instances/Databases on Spanner. See https://cloud.google.com/spanner/docs for an overview.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * google-auth >= 0.5.0
  * google-cloud-spanner >= 0.23.0


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
                <tr><td>configuration<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Configuration the instance should use. Examples are us-central1, asia-east1 and europe-west1.</div>        </td></tr>
                <tr><td>database_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of database contained on the instance.</div>        </td></tr>
                <tr><td>force_instance_delete<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>To delete an instance, this argument must exist and be true (along with state being equal to absent).</div>        </td></tr>
                <tr><td>instance_display_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of Instance to display.  If not specified, instance_id will be used instead.</div>        </td></tr>
                <tr><td>instance_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>GCP spanner instance name.</div>        </td></tr>
                <tr><td>node_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of nodes in the instance.  If not specified while creating an instance, node_count will be set to 1.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td></td>
        <td><div>State of the instance or database (absent, present). Applies to the most granular resource. If a database_name is specified we remove it.  If only instance_id is specified, that is what is removed.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create instance.
    gcspanner:
      instance_id: "{{ instance_id }}"
      configuration: "{{ configuration }}"
      state: present
      node_count: 1
    
    # Create database.
    gcspanner:
      instance_id: "{{ instance_id }}"
      configuration: "{{ configuration }}"
      database_name: "{{ database_name }}"
      state: present
    
    # Delete instance (and all databases)
    gcspanner:
      instance_id: "{{ instance_id }}"
      configuration: "{{ configuration }}"
      state: absent
      force_instance_delete: yes

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
        <td> instance_id </td>
        <td> Name of instance. </td>
        <td align=center> Always </td>
        <td align=center> str </td>
        <td align=center> myinstance </td>
    </tr>
            <tr>
        <td> database_name </td>
        <td> Name of database. </td>
        <td align=center> When database name is specified </td>
        <td align=center> str </td>
        <td align=center> mydatabase </td>
    </tr>
            <tr>
        <td> state </td>
        <td> The state of the instance or database. Value will be either 'absent' or 'present'. </td>
        <td align=center> Always </td>
        <td align=center> str </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> previous_values </td>
        <td> List of dictionaries containing previous values prior to update. </td>
        <td align=center> When an instance update has occurred and a field has been modified. </td>
        <td align=center> dict </td>
        <td align=center> 'previous_values': { 'instance': { 'instance_display_name': 'my-instance', 'node_count': 1 } } </td>
    </tr>
            <tr>
        <td> updated </td>
        <td> Boolean field to denote an update has occurred. </td>
        <td align=center> When an update has occurred. </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Changing the configuration on an existing instance is not supported.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
