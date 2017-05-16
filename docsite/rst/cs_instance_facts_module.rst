.. _cs_instance_facts:


cs_instance_facts - Gathering facts from the API of instances from Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Gathering facts from the API of an instance.


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
        <td><div>Account the instance is related to.</div></td></tr>
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
        <td><div>Domain the instance is related to.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name or display name of the instance.</div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Project the instance is related to.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - local_action:
        module: cs_instance_facts
        name: web-vm-1
    
    - debug: var=cloudstack_instance

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
        <td> cloudstack_instance.ssh_key </td>
        <td> Name of SSH key deployed to instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> key@work </td>
    </tr>
            <tr>
        <td> cloudstack_instance.name </td>
        <td> Name of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web-01 </td>
    </tr>
            <tr>
        <td> cloudstack_instance.password </td>
        <td> The password of the instance if exists. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Ge2oe7Do </td>
    </tr>
            <tr>
        <td> cloudstack_instance.default_ip </td>
        <td> Default IP address of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.23.37.42 </td>
    </tr>
            <tr>
        <td> cloudstack_instance.domain </td>
        <td> Domain the instance is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> cloudstack_instance.tags </td>
        <td> List of resource tags associated with the instance. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> [ { "key": "foo", "value": "bar" } ] </td>
    </tr>
            <tr>
        <td> cloudstack_instance.zone </td>
        <td> Name of zone the instance is in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> cloudstack_instance.state </td>
        <td> State of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Running </td>
    </tr>
            <tr>
        <td> cloudstack_instance.public_ip </td>
        <td> Public IP address with instance via static NAT rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.2.3.4 </td>
    </tr>
            <tr>
        <td> cloudstack_instance.display_name </td>
        <td> Display name of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web-01 </td>
    </tr>
            <tr>
        <td> cloudstack_instance.affinity_groups </td>
        <td> Affinity groups the instance is in. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [ "webservers" ] </td>
    </tr>
            <tr>
        <td> cloudstack_instance.id </td>
        <td> UUID of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 04589590-ac63-4ffc-93f5-b698b8ac38b6 </td>
    </tr>
            <tr>
        <td> cloudstack_instance.project </td>
        <td> Name of project the instance is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Production </td>
    </tr>
            <tr>
        <td> cloudstack_instance.instance_name </td>
        <td> Internal name of the instance (ROOT admin only). </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> i-44-3992-VM </td>
    </tr>
            <tr>
        <td> created </td>
        <td> Date of the instance was created. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2014-12-01T14:57:57+0100 </td>
    </tr>
            <tr>
        <td> cloudstack_instance.password_enabled </td>
        <td> True if password setting is enabled. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> cloudstack_instance.iso </td>
        <td> Name of ISO the instance was deployed with. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Debian-8-64bit </td>
    </tr>
            <tr>
        <td> cloudstack_instance.service_offering </td>
        <td> Name of the service offering the instance has. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2cpu_2gb </td>
    </tr>
            <tr>
        <td> cloudstack_instance.account </td>
        <td> Account the instance is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> cloudstack_instance.hypervisor </td>
        <td> Hypervisor related to this instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> KVM </td>
    </tr>
            <tr>
        <td> cloudstack_instance.security_groups </td>
        <td> Security groups the instance is in. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [ "default" ] </td>
    </tr>
            <tr>
        <td> cloudstack_instance.group </td>
        <td> Group name of the instance is related. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web </td>
    </tr>
            <tr>
        <td> cloudstack_instance.template </td>
        <td> Name of template the instance was deployed with. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Debian-8-64bit </td>
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

