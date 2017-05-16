.. _gcdns_zone:


gcdns_zone - Creates or removes zones in Google Cloud DNS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates or removes managed zones in Google Cloud DNS.


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
            <tr>
    <td>credentials_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to the JSON file associated with the service account email.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An arbitrary text string to use for the zone description.</div></td></tr>
            <tr>
    <td>pem_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to the PEM file associated with the service account email.</div><div>This option is deprecated and may be removed in a future release. Use <em>credentials_file</em> instead.</div></td></tr>
            <tr>
    <td>project_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The Google Cloud Platform project ID to use.</div></td></tr>
            <tr>
    <td>service_account_email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The e-mail address for a service account with access to Google Cloud DNS.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the given zone should or should not be present.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The DNS domain name of the zone.</div><div>This is NOT the Google Cloud DNS zone ID (e.g., example-com). If you attempt to specify a zone ID, this module will attempt to create a TLD and will fail.</div></br>
        <div style="font-size: small;">aliases: name<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Basic zone creation example.
    - name: Create a basic zone with the minimum number of parameters.
      gcdns_zone: zone=example.com
      
    # Zone removal example.
    - name: Remove a zone.
      gcdns_zone: zone=example.com state=absent
    
    # Zone creation with description
    - name: Creating a zone with a description
      gcdns_zone: zone=example.com description="This is an awesome zone"

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
        <td> state </td>
        <td> Whether the zone is present or absent </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> description </td>
        <td> The zone's description </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> This is an awesome zone </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> The zone's DNS name </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example.com. </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: See also :ref:`gcdns_record <gcdns_record>`.
.. note:: Zones that are newly created must still be set up with a domain registrar before they can be used.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

