.. _cs_zone_facts:


cs_zone_facts - Gathering facts of zones from Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Gathering facts from the API of a zone.


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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the zone.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - cs_zone_facts:
        name: ch-gva-1
      delegate_to: localhost
    
    - debug:
        var: cloudstack_zone

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
        <td> cloudstack_zone.zone_token </td>
        <td> Zone token </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ccb0a60c-79c8-3230-ab8b-8bdbe8c45bb7 </td>
    </tr>
            <tr>
        <td> cloudstack_zone.dns2_ipv6 </td>
        <td> Second IPv6 DNS for the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2001:4860:4860::8844 </td>
    </tr>
            <tr>
        <td> cloudstack_zone.tags </td>
        <td> List of resource tags associated with the zone. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> [{'key': 'foo', 'value': 'bar'}] </td>
    </tr>
            <tr>
        <td> cloudstack_zone.dhcp_provider </td>
        <td> DHCP provider for the zone </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> VirtualRouter </td>
    </tr>
            <tr>
        <td> cloudstack_zone.allocation_state </td>
        <td> State of the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Enabled </td>
    </tr>
            <tr>
        <td> cloudstack_zone.dns2 </td>
        <td> Second DNS for the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 8.8.4.4 </td>
    </tr>
            <tr>
        <td> cloudstack_zone.dns1 </td>
        <td> First DNS for the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 8.8.8.8 </td>
    </tr>
            <tr>
        <td> cloudstack_zone.id </td>
        <td> UUID of the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 04589590-ac63-4ffc-93f5-b698b8ac38b6 </td>
    </tr>
            <tr>
        <td> cloudstack_zone.network_type </td>
        <td> Network type for the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> basic </td>
    </tr>
            <tr>
        <td> cloudstack_zone.local_storage_enabled </td>
        <td> Local storage offering enabled. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> cloudstack_zone.internal_dns1 </td>
        <td> First internal DNS for the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 8.8.8.8 </td>
    </tr>
            <tr>
        <td> cloudstack_zone.guest_cidr_address </td>
        <td> Guest CIDR address for the zone </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.1.1.0/24 </td>
    </tr>
            <tr>
        <td> cloudstack_zone.internal_dns2 </td>
        <td> Second internal DNS for the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 8.8.4.4 </td>
    </tr>
            <tr>
        <td> cloudstack_zone.dns1_ipv6 </td>
        <td> First IPv6 DNS for the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2001:4860:4860::8888 </td>
    </tr>
            <tr>
        <td> cloudstack_zone.network_domain </td>
        <td> Network domain for the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example.com </td>
    </tr>
            <tr>
        <td> cloudstack_zone.name </td>
        <td> Name of the zone. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> zone01 </td>
    </tr>
            <tr>
        <td> cloudstack_zone.securitygroups_enabled </td>
        <td> Security groups support is enabled. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> cloudstack_zone.domain </td>
        <td> Domain the zone is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ROOT </td>
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
