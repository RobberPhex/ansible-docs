.. _digital_ocean_block_storage:


digital_ocean_block_storage - Create/destroy or attach/detach Block Storage volumes in DigitalOcean
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create/destroy Block Storage volume in DigitalOcean, or attach/detach Block Storage volume to a droplet.




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
                <tr><td>api_token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>DigitalOcean api token.</div>        </td></tr>
                <tr><td>block_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The size of the Block Storage volume in gigabytes. Required when command=create and state=present.</div>        </td></tr>
                <tr><td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>create</li><li>attach</li></ul></td>
        <td><div>Which operation do you want to perform.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of the Block Storage volume.</div>        </td></tr>
                <tr><td>droplet_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The droplet id you want to operate on. Required when command=attach.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The slug of the region where your Block Storage volume should be located in.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the target.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>The timeout in seconds used for polling DigitalOcean's API.</div>        </td></tr>
                <tr><td>volume_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the Block Storage volume.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create new Block Storage
    - digital_ocean_block_storage:
        state: present
        command: create
        api_token: <TOKEN>
        region: nyc1
        block_size: 10
        volume_name: nyc1-block-storage
    # Delete Block Storage
    - digital_ocean_block_storage:
        state: absent
        command: create
        api_token: <TOKEN>
        region: nyc1
        volume_name: nyc1-block-storage
    # Attach Block Storage to a Droplet
    - digital_ocean_block_storage:
        state: present
        command: attach
        api_token: <TOKEN>
        volume_name: nyc1-block-storage
        region: nyc1
        droplet_id: <ID>
    # Detach Block Storage from a Droplet
    - digital_ocean_block_storage:
        state: absent
        command: attach
        api_token: <TOKEN>
        volume_name: nyc1-block-storage
        region: nyc1
        droplet_id: <ID>

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
        <td> id </td>
        <td> Unique identifier of a Block Storage volume returned during creation. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> 69b25d9a-494c-12e6-a5af-001f53126b44 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Two environment variables can be used, DO_API_KEY and DO_API_TOKEN. They both refer to the v2 token.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
