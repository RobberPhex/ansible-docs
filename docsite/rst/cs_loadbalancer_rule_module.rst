.. _cs_loadbalancer_rule:


cs_loadbalancer_rule - Manages load balancer rules on Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add, update and remove load balancer rules.


Requirements
------------

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
        <td><div>Account the rule is related to.</div></td></tr>
            <tr>
    <td>algorithm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>source</td>
        <td><ul><li>source</li><li>roundrobin</li><li>leastconn</li></ul></td>
        <td><div>Load balancer algorithm</div><div>Required when using <code>state=present</code>.</div></td></tr>
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
    <td>cidr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>CIDR (full notation) to be used for firewall rule if required.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The description of the load balancer rule.</div></td></tr>
            <tr>
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Domain the rule is related to.</div></td></tr>
            <tr>
    <td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Public IP address from where the network traffic will be load balanced from.</div></br>
        <div style="font-size: small;">aliases: public_ip<div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the load balancer rule.</div></td></tr>
            <tr>
    <td>open_firewall<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether the firewall rule for public port should be created, while creating the new rule.</div><div>Use <span class='module'>cs_firewall</span> for managing firewall rules.</div></td></tr>
            <tr>
    <td>private_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The private port of the private ip address/virtual machine where the network traffic will be load balanced to.</div><div>Required when using <code>state=present</code>.</div><div>Can not be changed once the rule exists due API limitation.</div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the project the load balancer IP address is related to.</div></td></tr>
            <tr>
    <td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The protocol to be used on the load balancer</div></td></tr>
            <tr>
    <td>public_port<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The public port from where the network traffic will be load balanced from.</div><div>Required when using <code>state=present</code>.</div><div>Can not be changed once the rule exists due API limitation.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the rule.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the zone in which the rule shoud be created.</div><div>If not set, default zone is used.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a load balancer rule
    - local_action:
        module: cs_loadbalancer_rule
        name: balance_http
        public_ip: 1.2.3.4
        algorithm: leastconn
        public_port: 80
        private_port: 8080
    
    # update algorithm of an existing load balancer rule
    - local_action:
        module: cs_loadbalancer_rule
        name: balance_http
        public_ip: 1.2.3.4
        algorithm: roundrobin
        public_port: 80
        private_port: 8080
    
    # Delete a load balancer rule
    - local_action:
        module: cs_loadbalancer_rule
        name: balance_http
        public_ip: 1.2.3.4
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
        <td> project </td>
        <td> Name of project the rule is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Production </td>
    </tr>
            <tr>
        <td> domain </td>
        <td> Domain the rule is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> protocol </td>
        <td> Protocol of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> tcp </td>
    </tr>
            <tr>
        <td> algorithm </td>
        <td> Load balancer algorithm used. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> source </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone the rule is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> List of resource tags associated with the rule. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> [ { "key": "foo", "value": "bar" } ] </td>
    </tr>
            <tr>
        <td> public_port </td>
        <td> Public port. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 80 </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the rule is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> http-lb </td>
    </tr>
            <tr>
        <td> public_ip </td>
        <td> Public IP address. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.2.3.4 </td>
    </tr>
            <tr>
        <td> private_port </td>
        <td> Private IP address. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 80 </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Add </td>
    </tr>
            <tr>
        <td> cidr </td>
        <td> CIDR to forward traffic from. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> a6f7a5fc-43f8-11e5-a151-feff819cdc9f </td>
    </tr>
            <tr>
        <td> description </td>
        <td> Description of the rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> http load balancer rule </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
.. note:: This module supports check mode.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

