.. _exo_dns_domain:


exo_dns_domain - Manages domain records on Exoscale DNS API.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create and remove domain records.


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
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API key of the Exoscale DNS API.</div></td></tr>
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
        <td><div>Secret key of the Exoscale DNS API.</div></td></tr>
            <tr>
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>HTTP timeout to Exoscale DNS API.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the record.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the resource.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Validate SSL certs of the Exoscale DNS API.</div></td></tr>
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
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> record_count </td>
        <td> Number of records related to this domain </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 5 </td>
        </tr>
                <tr>
        <td> account_id </td>
        <td> Your account ID </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 34569 </td>
        </tr>
                <tr>
        <td> updated_at </td>
        <td> When the domain was updated last. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2016-08-12T15:24:23.989Z </td>
        </tr>
                <tr>
        <td> service_count </td>
        <td> Number of services </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 0 </td>
        </tr>
                <tr>
        <td> whois_protected </td>
        <td> Wheter the whois is protected or not </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> lockable </td>
        <td> Whether the domain is lockable or not </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> registrant_id </td>
        <td> ID of the registrant </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> None </td>
        </tr>
                <tr>
        <td> id </td>
        <td> ID of the domain </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 2016-08-12T15:24:23.989Z </td>
        </tr>
                <tr>
        <td> auto_renew </td>
        <td> Whether domain is auto renewed or not </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
        </tr>
                <tr>
        <td> user_id </td>
        <td> ID of the user </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> None </td>
        </tr>
                <tr>
        <td> name </td>
        <td> Domain name </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example.com </td>
        </tr>
                <tr>
        <td> created_at </td>
        <td> When the domain was created </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2016-08-12T15:24:23.989Z </td>
        </tr>
                <tr>
        <td> state </td>
        <td> State of the domain </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> hosted </td>
        </tr>
                <tr>
        <td> token </td>
        <td> Token </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> r4NzTRp6opIeFKfaFYvOd6MlhGyD07jl </td>
        </tr>
                <tr>
        <td> unicode_name </td>
        <td> Domain name as unicode </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example.com </td>
        </tr>
                <tr>
        <td> expires_on </td>
        <td> When the domain expires </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2016-08-12T15:24:23.989Z </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>

Notes
-----

.. note:: As Exoscale DNS uses the same API key and secret for all services, we reuse the config used for Exscale Compute based on CloudStack. The config is read from several locations, in the following order. The ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` environment variables. A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, A ``cloudstack.ini`` file in the current working directory. A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``.
.. note:: This module does not support multiple A records and will complain properly if you try.
.. note:: More information Exoscale DNS can be found on https://community.exoscale.ch/documentation/dns/.
.. note:: This module supports check mode and diff.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

