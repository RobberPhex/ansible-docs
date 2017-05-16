.. _cs_router:


cs_router - Manages routers on Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Start, restart, stop and destroy routers.
* ``state=present`` is not able to create routers, use :ref:`cs_network <cs_network>` instead.


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
        <td><div>Account the router is related to.</div>        </td></tr>
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
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Domain the router is related to.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the router.</div>        </td></tr>
                <tr><td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the project the router is related to.</div>        </td></tr>
                <tr><td>service_offering<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name or id of the service offering of the router.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>started</li><li>stopped</li><li>restarted</li></ul></td>
        <td><div>State of the router.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure the router has the desired service offering, no matter if
    # the router is running or not.
    - local_action:
        module: cs_router
        name: r-40-VM
        service_offering: System Offering for Software Router
    
    # Ensure started
    - local_action:
        module: cs_router
        name: r-40-VM
        state: started
    
    # Ensure started with desired service offering.
    # If the service offerings changes, router will be rebooted.
    - local_action:
        module: cs_router
        name: r-40-VM
        service_offering: System Offering for Software Router
        state: started
    
    # Ensure stopped
    - local_action:
        module: cs_router
        name: r-40-VM
        state: stopped
    
    # Remove a router
    - local_action:
        module: cs_router
        name: r-40-VM
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
        <td> domain </td>
        <td> Domain the router is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ROOT </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the router. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> r-40-VM </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone the router is in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> created </td>
        <td> Date of the router was created. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2014-12-01T14:57:57+0100 </td>
    </tr>
            <tr>
        <td> template_version </td>
        <td> Version of the system VM template. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 4.5.1 </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the router is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> admin </td>
    </tr>
            <tr>
        <td> requires_upgrade </td>
        <td> Whether the router needs to be upgraded to the new template. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the router. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Active </td>
    </tr>
            <tr>
        <td> role </td>
        <td> Role of the router. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> VIRTUAL_ROUTER </td>
    </tr>
            <tr>
        <td> service_offering </td>
        <td> Name of the service offering the router has. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> System Offering For Software Router </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the router. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 04589590-ac63-4ffc-93f5-b698b8ac38b6 </td>
    </tr>
            <tr>
        <td> redundant_state </td>
        <td> Redundant state of the router. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> UNKNOWN </td>
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
