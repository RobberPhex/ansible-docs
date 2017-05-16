.. _cs_resourcelimit:


cs_resourcelimit - Manages resource limits on Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage limits of resources for domains, accounts and projects.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * cs >= 0.6.10


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
    <td>account<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Account the resource is related to.</div></td></tr>
            <tr>
    <td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div></td></tr>
            <tr>
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td><ul></ul></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div></td></tr>
            <tr>
    <td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Secret key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>HTTP timeout.</div></td></tr>
            <tr>
    <td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div></td></tr>
            <tr>
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Domain the resource is related to.</div></td></tr>
            <tr>
    <td>limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>-1</td>
        <td><ul></ul></td>
        <td><div>Maximum number of the resource.</div><div>Default is unlimited <code>-1</code>.</div></br>
        <div style="font-size: small;">aliases: max<div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the project the resource is related to.</div></td></tr>
            <tr>
    <td>resource_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>instance</li><li>ip_address</li><li>volume</li><li>snapshot</li><li>template</li><li>network</li><li>vpc</li><li>cpu</li><li>memory</li><li>primary_storage</li><li>secondary_storage</li></ul></td>
        <td><div>Type of the resource.</div></br>
        <div style="font-size: small;">aliases: type<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Update a resource limit for instances of a domain
    local_action:
      module: cs_resourcelimit
      type: instance
      limit: 10
      domain: customers
    
    # Update a resource limit for instances of an account
    local_action:
      module: cs_resourcelimit
      type: instance
      limit: 12
      account: moserre
      domain: customers

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
        <td> project </td>
        <td> Project the resource is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example project </td>
    </tr>
            <tr>
        <td> domain </td>
        <td> Domain the resource is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> limit </td>
        <td> Maximum number of the resource. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> -1 </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the resource is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> recource_type </td>
        <td> Type of the resource </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> instance </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
.. note:: A detailed guide about cloudstack modules can be found on http://docs.ansible.com/ansible/guide_cloudstack.html
.. note:: This module supports check mode.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

