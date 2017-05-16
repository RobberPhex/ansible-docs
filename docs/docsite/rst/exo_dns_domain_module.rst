.. _exo_dns_domain:


exo_dns_domain - Manages domain records on Exoscale DNS API.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create and remove domain records.


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
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>API key of the Exoscale DNS API.</div>        </td></tr>
                <tr><td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div>        </td></tr>
                <tr><td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Secret key of the Exoscale DNS API.</div>        </td></tr>
                <tr><td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>HTTP timeout to Exoscale DNS API.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the record.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the resource.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Validate SSL certs of the Exoscale DNS API.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a domain.
    - local_action:
        module: exo_dns_domain
        name: example.com
    
    # Remove a domain.
    - local_action:
        module: exo_dns_domain
        name: example.com
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
        <td> exo_dns_domain </td>
        <td> API domain results </td>
        <td align=center> success </td>
        <td align=center> complex </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - As Exoscale DNS uses the same API key and secret for all services, we reuse the config used for Exscale Compute based on CloudStack. The config is read from several locations, in the following order. The ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` environment variables. A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, A ``cloudstack.ini`` file in the current working directory. A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``.
    - This module does not support multiple A records and will complain properly if you try.
    - More information Exoscale DNS can be found on https://community.exoscale.ch/documentation/dns/.
    - This module supports check mode and diff.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
