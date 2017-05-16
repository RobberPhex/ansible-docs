.. _digital_ocean_domain:


digital_ocean_domain - Create/delete a DNS record in DigitalOcean
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create/delete a DNS record in DigitalOcean.


Requirements
------------

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
            <tr>
    <td>api_token<br/><div style="font-size: small;"> (added in 1.9.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>DigitalOcean api token.</div></td></tr>
            <tr>
    <td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Numeric, the droplet id you want to operate on.</div></td></tr>
            <tr>
    <td>ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The IP address to point a domain at.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>String, this is the name of the droplet - must be formatted by hostname rules, or the name of a SSH key, or the name of a domain.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the target.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a domain record
    
    - digital_ocean_domain: >
          state=present
          name=my.digitalocean.domain
          ip=127.0.0.1
    
    # Create a droplet and a corresponding domain record
    
    - digital_ocean: >
          state=present
          name=test_droplet
          size_id=1gb
          region_id=sgp1
          image_id=ubuntu-14-04-x64
      register: test_droplet
    
    - digital_ocean_domain: >
          state=present
          name={{ test_droplet.droplet.name }}.my.domain
          ip={{ test_droplet.droplet.ip_address }}


Notes
-----

.. note:: Two environment variables can be used, DO_API_KEY and DO_API_TOKEN. They both refer to the v2 token.
.. note:: As of Ansible 1.9.5 and 2.0, Version 2 of the DigitalOcean API is used, this removes ``client_id`` and ``api_key`` options in favor of ``api_token``.
.. note:: If you are running Ansible 1.9.4 or earlier you might not be able to use the included version of this module as the API version used has been retired.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

