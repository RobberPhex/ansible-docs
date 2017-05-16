.. _digital_ocean_tag:


digital_ocean_tag - Create and remove tag(s) to DigitalOcean resource.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create and remove tag(s) to DigitalOcean resource.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6


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
    <td>api_token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>DigitalOcean api token.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the tag. The supported characters for names include alphanumeric characters, dashes, and underscores.</div></td></tr>
            <tr>
    <td>resource_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ID of the resource to operate on.</div></td></tr>
            <tr>
    <td>resource_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>droplet</td>
        <td><ul><li>droplet</li></ul></td>
        <td><div>The type of resource to operate on. Currently only tagging of droplets is supported.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the tag should be present or absent on the resource.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: create a tag
      digital_ocean_tag:
        name: production
        state: present
    
    - name: tag a resource; creating the tag if it does not exists
      digital_ocean_tag:
        name: "{{ item }}"
        resource_id: YYY
        state: present
      with_items:
        - staging
        - dbserver
    
    - name: untag a resource
      digital_ocean_tag:
        name: staging
        resource_id: YYY
        state: absent
    
    # Deleting a tag also untags all the resources that have previously been
    # tagged with it
    - name: remove a tag
      digital_ocean_tag:
        name: dbserver
        state: absent

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
        <td> data </td>
        <td> a DigitalOcean Tag resource </td>
        <td align=center> success and no resource constraint </td>
        <td align=center> dict </td>
        <td align=center> {'tag': {'name': 'awesome', 'resources': {'droplets': {'count': 0, 'last_tagged': None}}}} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Two environment variables can be used, DO_API_KEY and DO_API_TOKEN. They both refer to the v2 token.
.. note:: As of Ansible 2.0, Version 2 of the DigitalOcean API is used.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

