.. _cs_iso:


cs_iso - Manages ISO images on Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Register and remove ISO images.


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
        <td><div>Account the ISO is related to.</div>        </td></tr>
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
                <tr><td>bootable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Register the ISO to be bootable. Only used if <code>state</code> is present.</div>        </td></tr>
                <tr><td>checksum<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The MD5 checksum value of this ISO. If set, we search by checksum instead of name.</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Domain the ISO is related to.</div>        </td></tr>
                <tr><td>is_dynamically_scalable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Register the ISO having XS/VMWare tools installed inorder to support dynamic scaling of VM cpu/memory. Only used if <code>state</code> is present.</div>        </td></tr>
                <tr><td>is_featured<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Register the ISO to be featured. Only used if <code>state</code> is present.</div>        </td></tr>
                <tr><td>is_public<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Register the ISO to be publicly available to all users. Only used if <code>state</code> is present.</div>        </td></tr>
                <tr><td>is_ready<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This flag is used for searching existing ISOs. If set to <code>true</code>, it will only list ISO ready for deployment e.g. successfully downloaded and installed. Recommended to set it to <code>false</code>.</div>        </td></tr>
                <tr><td>iso_filter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>self</td>
        <td><ul><li>featured</li><li>self</li><li>selfexecutable</li><li>sharedexecutable</li><li>executable</li><li>community</li></ul></td>
        <td><div>Name of the filter used to search for the ISO.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the ISO.</div>        </td></tr>
                <tr><td>os_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the OS that best represents the OS of this ISO. If the iso is bootable this parameter needs to be passed. Required if <code>state</code> is present.</div>        </td></tr>
                <tr><td>poll_async<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Poll async jobs until job has finished.</div>        </td></tr>
                <tr><td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the project the ISO to be registered in.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the ISO.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL where the ISO can be downloaded from. Required if <code>state</code> is present.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the zone you wish the ISO to be registered or deleted from. If not specified, first zone found will be used.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Register an ISO if ISO name does not already exist.
    - local_action:
        module: cs_iso
        name: Debian 7 64-bit
        url: http://mirror.switch.ch/ftp/mirror/debian-cd/current/amd64/iso-cd/debian-7.7.0-amd64-netinst.iso
        os_type: Debian GNU/Linux 7(64-bit)
    
    # Register an ISO with given name if ISO md5 checksum does not already exist.
    - local_action:
        module: cs_iso
        name: Debian 7 64-bit
        url: http://mirror.switch.ch/ftp/mirror/debian-cd/current/amd64/iso-cd/debian-7.7.0-amd64-netinst.iso
        os_type: Debian GNU/Linux 7(64-bit)
        checksum: 0b31bccccb048d20b551f70830bb7ad0
    
    # Remove an ISO by name
    - local_action:
        module: cs_iso
        name: Debian 7 64-bit
        state: absent
    
    # Remove an ISO by checksum
    - local_action:
        module: cs_iso
        name: Debian 7 64-bit
        checksum: 0b31bccccb048d20b551f70830bb7ad0
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
        <td> display_text </td>
        <td> Text to be displayed of the ISO. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Debian 7.7 64-bit minimal 2015-03-19 </td>
    </tr>
            <tr>
        <td> status </td>
        <td> Status of the ISO. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Successfully Installed </td>
    </tr>
            <tr>
        <td> domain </td>
        <td> Domain the ISO is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the ISO. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Debian 7 64-bit </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone the ISO is registered in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> zuerich </td>
    </tr>
            <tr>
        <td> created </td>
        <td> Date of registering. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2015-03-29T14:57:06+0200 </td>
    </tr>
            <tr>
        <td> checksum </td>
        <td> MD5 checksum of the ISO. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 0b31bccccb048d20b551f70830bb7ad0 </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the ISO is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> project </td>
        <td> Project the ISO is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example project </td>
    </tr>
            <tr>
        <td> is_ready </td>
        <td> True if the ISO is ready to be deployed from. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the ISO. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> a6f7a5fc-43f8-11e5-a151-feff819cdc9f </td>
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
