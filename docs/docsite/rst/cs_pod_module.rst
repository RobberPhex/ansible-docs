.. _cs_pod:


cs_pod - Manages pods on Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update, delete pods.


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
                <tr><td>end_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ending IP address for the Pod.</div>        </td></tr>
                <tr><td>gateway<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Gateway for the Pod.</div><div>Required on <code>state=present</code></div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>uuid of the exising pod.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the pod.</div>        </td></tr>
                <tr><td>netmask<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Netmask for the Pod.</div><div>Required on <code>state=present</code></div>        </td></tr>
                <tr><td>start_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Starting IP address for the Pod.</div><div>Required on <code>state=present</code></div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>enabled</li><li>disabled</li><li>absent</li></ul></td>
        <td><div>State of the pod.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the zone in which the pod belongs to.</div><div>If not set, default zone is used.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a pod is present
    - local_action:
        module: cs_pod
        name: pod1
        zone: ch-zrh-ix-01
        start_ip: 10.100.10.101
        gateway: 10.100.10.1
        netmask: 255.255.255.0
    
    # Ensure a pod is disabled
    - local_action:
        module: cs_pod
        name: pod1
        zone: ch-zrh-ix-01
        state: disabled
    
    # Ensure a pod is enabled
    - local_action:
        module: cs_pod
        name: pod1
        zone: ch-zrh-ix-01
        state: enabled
    
    # Ensure a pod is absent
    - local_action:
        module: cs_pod
        name: pod1
        zone: ch-zrh-ix-01
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
        <td> name </td>
        <td> Name of the pod. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> pod01 </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone the pod is in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> gateway </td>
        <td> Gateway of the pod. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.100.1.1 </td>
    </tr>
            <tr>
        <td> netmask </td>
        <td> Netmask of the pod. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 255.255.255.0 </td>
    </tr>
            <tr>
        <td> end_ip </td>
        <td> Ending IP of the pod. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.100.1.254 </td>
    </tr>
            <tr>
        <td> start_ip </td>
        <td> Starting IP of the pod. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.100.1.101 </td>
    </tr>
            <tr>
        <td> allocation_state </td>
        <td> State of the pod. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Enabled </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the pod. </td>
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
