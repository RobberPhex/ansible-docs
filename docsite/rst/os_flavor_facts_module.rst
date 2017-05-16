.. _os_flavor_facts:


os_flavor_facts - Retrieve facts about one or more flavors
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Retrieve facts about available OpenStack instance flavors. By default, facts about ALL flavors are retrieved. Filters can be applied to get facts for only matching flavors. For example, you can filter on the amount of RAM available to the flavor, or the number of virtual CPUs available to the flavor, or both. When specifying multiple filters, *ALL* filters must match on a flavor before that flavor is returned as a fact.


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
    <td>limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Limits the number of flavors returned. All matching flavors are returned by default.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A flavor name. Cannot be used with <em>ram</em> or <em>vcpus</em>.</div></td></tr>
            <tr>
    <td>ram<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A string used for filtering flavors based on the amount of RAM (in MB) desired. This string accepts the following special values: 'MIN' (return flavors with the minimum amount of RAM), and 'MAX' (return flavors with the maximum amount of RAM).</div><div>A specific amount of RAM may also be specified. Any flavors with this exact amount of RAM will be returned.</div><div>A range of acceptable RAM may be given using a special syntax. Simply prefix the amount of RAM with one of these acceptable range values: '&lt;', '&gt;', '&lt;=', '&gt;='. These values represent less than, greater than, less than or equal to, and greater than or equal to, respectively.</div></td></tr>
            <tr>
    <td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the region.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td><ul></ul></td>
        <td><div>How long should ansible wait for the requested resource.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether or not SSL API requests should be verified.</div></br>
        <div style="font-size: small;">aliases: verify<div></td></tr>
            <tr>
    <td>vcpus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A string used for filtering flavors based on the number of virtual CPUs desired. Format is the same as the <em>ram</em> parameter.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Should ansible wait until the requested resource is complete.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Gather facts about all available flavors
    - os_flavor_facts:
        cloud: mycloud
    
    # Gather facts for the flavor named "xlarge-flavor"
    - os_flavor_facts:
        cloud: mycloud
        name: "xlarge-flavor"
    
    # Get all flavors that have exactly 512 MB of RAM.
    - os_flavor_facts:
        cloud: mycloud
        ram: "512"
    
    # Get all flavors that have 1024 MB or more of RAM.
    - os_flavor_facts:
        cloud: mycloud
        ram: ">=1024"
    
    # Get a single flavor that has the minimum amount of RAM. Using the 'limit'
    # option will guarantee only a single flavor is returned.
    - os_flavor_facts:
        cloud: mycloud
        ram: "MIN"
        limit: 1
    
    # Get all flavors with 1024 MB of RAM or more, AND exactly 2 virtual CPUs.
    - os_flavor_facts:
        cloud: mycloud
        ram: ">=1024"
        vcpus: "2"

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
        <td> openstack_flavors </td>
        <td> Dictionary describing the flavors. </td>
        <td align=center> On success. </td>
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
        <td> name </td>
        <td> Flavor name. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> tiny </td>
        </tr>
                <tr>
        <td> ram </td>
        <td> Amount of memory, in MB. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 1024 </td>
        </tr>
                <tr>
        <td> ephemeral </td>
        <td> Ephemeral space size, in GB. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 10 </td>
        </tr>
                <tr>
        <td> vcpus </td>
        <td> Number of virtual CPUs. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 2 </td>
        </tr>
                <tr>
        <td> swap </td>
        <td> Swap space size, in MB. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 100 </td>
        </tr>
                <tr>
        <td> is_public </td>
        <td> Make flavor accessible to the public. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> disk </td>
        <td> Size of local disk, in GB. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 10 </td>
        </tr>
                <tr>
        <td> id </td>
        <td> Flavor ID. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 515256b8-7027-4d73-aa54-4e30a4a4a339 </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>

Notes
-----

.. note:: This module creates a new top-level ``openstack_flavors`` fact, which contains a list of unsorted flavors.
.. note:: The standard OpenStack environment variables, such as ``OS_USERNAME`` may be used instead of providing explicit values.
.. note:: Auth information is driven by os-client-config, which means that values can come from a yaml config file in /etc/ansible/openstack.yaml, /etc/openstack/clouds.yaml or ~/.config/openstack/clouds.yaml, then from standard environment variables, then finally by explicit parameters in plays. More information can be found at http://docs.openstack.org/developer/os-client-config


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

