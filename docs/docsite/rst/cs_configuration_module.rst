.. _cs_configuration:


cs_configuration - Manages configuration on Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages global, zone, account, storage and cluster configurations.


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
                <tr><td>account<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ensure the value for corresponding account.</div>        </td></tr>
                <tr><td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div>        </td></tr>
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>API key of the CloudStack API.</div>        </td></tr>
                <tr><td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div>        </td></tr>
                <tr><td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Secret key of the CloudStack API.</div>        </td></tr>
                <tr><td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>HTTP timeout.</div>        </td></tr>
                <tr><td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div>        </td></tr>
                <tr><td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ensure the value for corresponding cluster.</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ROOT</td>
        <td></td>
        <td><div>Domain the account is related to.</div><div>Only considered if <code>account</code> is used.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the configuration.</div>        </td></tr>
                <tr><td>storage<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ensure the value for corresponding storage pool.</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Value of the configuration.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ensure the value for corresponding zone.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure global configuration
    - local_action:
        module: cs_configuration
        name: router.reboot.when.outofband.migrated
        value: false
    
    # Ensure zone configuration
    - local_action:
        module: cs_configuration
        name: router.reboot.when.outofband.migrated
        zone: ch-gva-01
        value: true
    
    # Ensure storage configuration
    - local_action:
        module: cs_configuration
        name: storage.overprovisioning.factor
        storage: storage01
        value: 2.0
    
    # Ensure account configuration
    - local_action:
        module: cs_configuration
        name: allow.public.user.templates
        value: false
        account: acme inc
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
        <td> category </td>
        <td> Category of the configuration. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Advanced </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account of the configuration. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> admin </td>
    </tr>
            <tr>
        <td> description </td>
        <td> Description of the configuration. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Setup the host to do multipath </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Zone of the configuration. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-01 </td>
    </tr>
            <tr>
        <td> storage </td>
        <td> Storage of the configuration. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> storage01 </td>
    </tr>
            <tr>
        <td> Domain </td>
        <td> Domain of account of the configuration. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ROOT </td>
    </tr>
            <tr>
        <td> value </td>
        <td> Value of the configuration. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 0.75 </td>
    </tr>
            <tr>
        <td> cluster </td>
        <td> Cluster of the configuration. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> cluster01 </td>
    </tr>
            <tr>
        <td> scope </td>
        <td> Scope (zone/cluster/storagepool/account) of the parameter that needs to be updated. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> storagepool </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the configuration. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> zone.vlan.capacity.notificationthreshold </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
    - A detailed guide about cloudstack modules can be found on http://docs.ansible.com/ansible/guide_cloudstack.html
    - This module supports check mode.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
