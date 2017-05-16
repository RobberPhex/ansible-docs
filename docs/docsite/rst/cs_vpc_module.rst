.. _cs_vpc:


cs_vpc - Manages VPCs on Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update and delete VPCs.


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
        <td><div>Account the VPC is related to.</div>        </td></tr>
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
                <tr><td>cidr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>CIDR of the VPC, e.g. 10.1.0.0/16</div><div>All VPC guest networks' CIDRs must be within this CIDR.</div><div>Required on <code>state=present</code>.</div>        </td></tr>
                <tr><td>display_text<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Display text of the VPC.</div><div>If not set, <code>name</code> will be used for creating.</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Domain the VPC is related to.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the VPC.</div>        </td></tr>
                <tr><td>network_domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Network domain for the VPC.</div><div>All networks inside the VPC will belong to this domain.</div>        </td></tr>
                <tr><td>poll_async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Poll async jobs until job has finished.</div>        </td></tr>
                <tr><td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the project the VPC is related to.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>restarted</li></ul></td>
        <td><div>State of the VPC.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of tags. Tags are a list of dictionaries having keys <code>key</code> and <code>value</code>.</div><div>For deleting all tags, set an empty list e.g. <code>tags: []</code>.</div></br>
    <div style="font-size: small;">aliases: tag<div>        </td></tr>
                <tr><td>vpc_offering<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the VPC offering.</div><div>If not set, default VPC offering is used.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the zone.</div><div>If not set, default zone is used.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a VPC is present
    - local_action:
        module: cs_vpc
        name: my_vpc
        display_text: My example VPC
        cidr: 10.10.0.0/16
    
    # Ensure a VPC is absent
    - local_action:
        module: cs_vpc
        name: my_vpc
        state: absent
    
    # Ensure a VPC is restarted
    - local_action:
        module: cs_vpc
        name: my_vpc
        state: restarted

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
        <td> display_text </td>
        <td> Display text of the VPC. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> My example VPC </td>
    </tr>
            <tr>
        <td> domain </td>
        <td> Domain the VPC is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the VPC. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> my_vpc </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone the VPC is in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> List of resource tags associated with the VPC. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> [ { "key": "foo", "value": "bar" } ] </td>
    </tr>
            <tr>
        <td> region_level_vpc </td>
        <td> Whether the VPC is region level or not. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> redundant_vpc_router </td>
        <td> Whether the VPC has redundant routers or not. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> distributed_vpc_router </td>
        <td> Whether the VPC uses distributed router or not. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> project </td>
        <td> Name of project the VPC is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Production </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the VPC. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Enabled </td>
    </tr>
            <tr>
        <td> restart_required </td>
        <td> Wheter the VPC router needs a restart or not. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the VPC is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> cidr </td>
        <td> CIDR of the VPC. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.10.0.0/16 </td>
    </tr>
            <tr>
        <td> network_domain </td>
        <td> Network domain of the VPC. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example.com </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the VPC. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 04589590-ac63-4ffc-93f5-b698b8ac38b6 </td>
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
