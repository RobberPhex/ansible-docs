.. _cs_volume:


cs_volume - Manages volumes on Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, destroy, attach, detach volumes.


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
        <td><div>Account the volume is related to.</div></td></tr>
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
    <td>custom_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Custom id to the resource.</div><div>Allowed to Root Admins only.</div></td></tr>
            <tr>
    <td>disk_offering<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the disk offering to be used.</div><div>Required one of <code>disk_offering</code>, <code>snapshot</code> if volume is not already <code>state=present</code>.</div></td></tr>
            <tr>
    <td>display_volume<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether to display the volume to the end user or not.</div><div>Allowed to Root Admins only.</div></td></tr>
            <tr>
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the domain the volume to be deployed in.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Force removal of volume even it is attached to a VM.</div><div>Considered on <code>state=absnet</code> only.</div></td></tr>
            <tr>
    <td>max_iops<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Max iops</div></td></tr>
            <tr>
    <td>min_iops<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Min iops</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the volume.</div><div><code>name</code> can only contain ASCII letters.</div></td></tr>
            <tr>
    <td>poll_async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Poll async jobs until job has finished.</div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the project the volume to be deployed in.</div></td></tr>
            <tr>
    <td>shrink_ok<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether to allow to shrink the volume.</div></td></tr>
            <tr>
    <td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Size of disk in GB</div></td></tr>
            <tr>
    <td>snapshot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The snapshot name for the disk volume.</div><div>Required one of <code>disk_offering</code>, <code>snapshot</code> if volume is not already <code>state=present</code>.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>attached</li><li>detached</li></ul></td>
        <td><div>State of the volume.</div></td></tr>
            <tr>
    <td>vm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the virtual machine to attach the volume to.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the zone in which the volume should be deployed.</div><div>If not set, default zone is used.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create volume within project, zone with specified storage options
    - local_action:
        module: cs_volume
        name: web-vm-1-volume
        project: Integration
        zone: ch-zrh-ix-01
        disk_offering: PerfPlus Storage
        size: 20
    
    # Create/attach volume to instance
    - local_action:
        module: cs_volume
        name: web-vm-1-volume
        disk_offering: PerfPlus Storage
        size: 20
        vm: web-vm-1
        state: attached
    
    # Detach volume
    - local_action:
        module: cs_volume
        name: web-vm-1-volume
        state: detached
    
    # Remove volume
    - local_action:
        module: cs_volume
        name: web-vm-1-volume
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
        <td> Domain the volume belongs to </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> group </td>
        <td> Group the volume belongs to </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the volume. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web-volume-01 </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone the volume is in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> created </td>
        <td> Date of the volume was created. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2014-12-01T14:57:57+0100 </td>
    </tr>
            <tr>
        <td> attached </td>
        <td> Date of the volume was attached. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2014-12-01T14:57:57+0100 </td>
    </tr>
            <tr>
        <td> vm </td>
        <td> Name of the vm the volume is attached to (not returned when detached) </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web-01 </td>
    </tr>
            <tr>
        <td> project </td>
        <td> Project the volume belongs to </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Production </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the volume </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Attached </td>
    </tr>
            <tr>
        <td> display_name </td>
        <td> Display name of the volume. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web-volume-01 </td>
    </tr>
            <tr>
        <td> size </td>
        <td> Size of disk volume. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 20 </td>
    </tr>
            <tr>
        <td> type </td>
        <td> Disk volume type. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> DATADISK </td>
    </tr>
            <tr>
        <td> id </td>
        <td> ID of the volume. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> None </td>
    </tr>
            <tr>
        <td> device_id </td>
        <td> Id of the device on user vm the volume is attached to (not returned when detached) </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
.. note:: A detailed guide about cloudstack modules can be found on http://docs.ansible.com/ansible/guide_cloudstack.html
.. note:: This module supports check mode.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

