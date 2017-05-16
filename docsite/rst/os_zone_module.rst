.. _os_zone:


os_zone - Manage OpenStack DNS zones
++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage OpenStack DNS zones. Zones can be created, deleted or updated. Only the *email*, *description*, *ttl* and *masters* values can be updated.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * python >= 2.7
  * shade


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
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>How long should the socket layer wait before timing out for API calls. If this is omitted, nothing will be passed to the requests library.</div></td></tr>
            <tr>
    <td>auth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary containing auth information as needed by the cloud's auth plugin strategy. For the default <em>password</em> plugin, this would contain <em>auth_url</em>, <em>username</em>, <em>password</em>, <em>project_name</em> and any information about domains if the cloud supports them. For other plugins, this param will need to contain whatever parameters that auth plugin requires. This parameter is not needed if a named cloud is provided or OpenStack OS_* environment variables are present.</div></td></tr>
            <tr>
    <td>auth_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>password</td>
        <td><ul></ul></td>
        <td><div>Name of the auth plugin to use. If the cloud uses something other than password authentication, the name of the plugin should be indicated here and the contents of the <em>auth</em> parameter should be updated accordingly.</div></td></tr>
            <tr>
    <td>availability_zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the availability zone.</div></td></tr>
            <tr>
    <td>cacert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A path to a CA Cert bundle that can be used as part of verifying SSL API requests.</div></td></tr>
            <tr>
    <td>cert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A path to a client certificate to use as part of the SSL transaction</div></td></tr>
            <tr>
    <td>cloud<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Named cloud to operate against. Provides default values for <em>auth</em> and <em>auth_type</em>. This parameter is not needed if <em>auth</em> is provided or if OpenStack OS_* environment variables are present.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Zone description</div></td></tr>
            <tr>
    <td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Email of the zone owner (only applies if zone_type is primary)</div></td></tr>
            <tr>
    <td>endpoint_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>public</td>
        <td><ul><li>public</li><li>internal</li><li>admin</li></ul></td>
        <td><div>Endpoint URL type to fetch from the service catalog.</div></td></tr>
            <tr>
    <td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A path to a client key to use as part of the SSL transaction</div></td></tr>
            <tr>
    <td>masters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Master nameservers (only applies if zone_type is secondary)</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Zone name</div></td></tr>
            <tr>
    <td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the region.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Should the resource be present or absent.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td><ul></ul></td>
        <td><div>How long should ansible wait for the requested resource.</div></td></tr>
            <tr>
    <td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>TTL (Time To Live) value in seconds</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether or not SSL API requests should be verified.</div></br>
        <div style="font-size: small;">aliases: verify<div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Should ansible wait until the requested resource is complete.</div></td></tr>
            <tr>
    <td>zone_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>primary</li><li>secondary</li></ul></td>
        <td><div>Zone type</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a zone named "example.net"
    - os_zone:
        cloud: mycloud
        state: present
        name: example.net.
        zone_type: primary
        email: test@example.net
        description: Test zone
        ttl: 3600
    
    # Update the TTL on existing "example.net." zone
    - os_zone:
        cloud: mycloud
        state: present
        name: example.net.
        ttl: 7200
    
    # Delete zone named "example.net."
    - os_zone:
        cloud: mycloud
        state: absent
        name: example.net.

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
        <td> zone </td>
        <td> Dictionary describing the zone. </td>
        <td align=center> On success when I(state) is 'present'. </td>
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
        <td> masters </td>
        <td> Zone master nameservers </td>
        <td align=center>  </td>
        <td align=center> list </td>
        <td align=center> [] </td>
        </tr>
                <tr>
        <td> description </td>
        <td> Zone description </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> Test description </td>
        </tr>
                <tr>
        <td> name </td>
        <td> Zone name </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> example.net. </td>
        </tr>
                <tr>
        <td> ttl </td>
        <td> Zone TTL value </td>
        <td align=center>  </td>
        <td align=center> int </td>
        <td align=center> 3600 </td>
        </tr>
                <tr>
        <td> type </td>
        <td> Zone type </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> PRIMARY </td>
        </tr>
                <tr>
        <td> id </td>
        <td> Unique zone ID </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> c1c530a3-3619-46f3-b0f6-236927b2618c </td>
        </tr>
                <tr>
        <td> email </td>
        <td> Zone owner email </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> test@example.net </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>

Notes
-----

.. note:: The standard OpenStack environment variables, such as ``OS_USERNAME`` may be used instead of providing explicit values.
.. note:: Auth information is driven by os-client-config, which means that values can come from a yaml config file in /etc/ansible/openstack.yaml, /etc/openstack/clouds.yaml or ~/.config/openstack/clouds.yaml, then from standard environment variables, then finally by explicit parameters in plays. More information can be found at http://docs.openstack.org/developer/os-client-config


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

