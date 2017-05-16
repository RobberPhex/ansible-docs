.. _glance_image:


glance_image - Add/Delete images from glance
++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2

DEPRECATED
----------

Deprecated in 1.10. Use :ref:`os_image <os_image>` instead.

Synopsis
--------

* Add or Remove images from the glance repository.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * python-glanceclient
  * python-keystoneclient


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
                <tr><td>auth_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td></td>
        <td><div>The keystone url for authentication</div>        </td></tr>
                <tr><td>container_format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>bare</td>
        <td></td>
        <td><div>The format of the container</div>        </td></tr>
                <tr><td>copy_from<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A url from where the image can be downloaded, mutually exclusive with file parameter</div>        </td></tr>
                <tr><td>disk_format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>qcow2</td>
        <td></td>
        <td><div>The format of the disk that is getting uploaded</div>        </td></tr>
                <tr><td>endpoint_type<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td>publicURL</td>
        <td><ul><li>publicURL</li><li>internalURL</li></ul></td>
        <td><div>The name of the glance service's endpoint URL type</div>        </td></tr>
                <tr><td>file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The path to the file which has to be uploaded, mutually exclusive with copy_from</div>        </td></tr>
                <tr><td>is_public<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td></td>
        <td><div>Whether the image can be accessed publicly</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>yes</td>
        <td></td>
        <td><div>Password of login user</div>        </td></tr>
                <tr><td>login_tenant_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>yes</td>
        <td></td>
        <td><div>The tenant name of the login user</div>        </td></tr>
                <tr><td>login_username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>admin</td>
        <td></td>
        <td><div>login username to authenticate to keystone</div>        </td></tr>
                <tr><td>min_disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The minimum disk space required to deploy this image</div>        </td></tr>
                <tr><td>min_ram<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The minimum ram required to deploy this image</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>Name that has to be given to the image</div>        </td></tr>
                <tr><td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The owner of the image</div>        </td></tr>
                <tr><td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Name of the region</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td></td>
        <td><div>The time to wait for the image process to complete in seconds</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Upload an image from an HTTP URL
      glance_image:
        login_username: admin
        login_password: passme
        login_tenant_name: admin
        name: cirros
        container_format: bare
        disk_format: qcow2
        state: present
        copy_from: http://launchpad.net/cirros/trunk/0.3.0/+download/cirros-0.3.0-x86_64-disk.img




For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
