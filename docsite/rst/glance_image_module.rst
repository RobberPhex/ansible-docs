.. _glance_image:


glance_image - Add/Delete images from glance
++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Add or Remove images from the glance repository.

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
    <td>auth_url</td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td><ul></ul></td>
        <td>The keystone url for authentication</td>
    </tr>
            <tr>
    <td>container_format</td>
    <td>no</td>
    <td>bare</td>
        <td><ul></ul></td>
        <td>The format of the container</td>
    </tr>
            <tr>
    <td>copy_from</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>A url from where the image can be downloaded, mutually exclusive with file parameter</td>
    </tr>
            <tr>
    <td>disk_format</td>
    <td>no</td>
    <td>qcow2</td>
        <td><ul></ul></td>
        <td>The format of the disk that is getting uploaded</td>
    </tr>
            <tr>
    <td>endpoint_type</td>
    <td>no</td>
    <td>publicURL</td>
        <td><ul><li>publicURL</li><li>internalURL</li></ul></td>
        <td>The name of the glance service's endpoint URL type (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>file</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The path to the file which has to be uploaded, mutually exclusive with copy_from</td>
    </tr>
            <tr>
    <td>is_public</td>
    <td>no</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td>Whether the image can be accessed publicly</td>
    </tr>
            <tr>
    <td>login_password</td>
    <td>yes</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td>Password of login user</td>
    </tr>
            <tr>
    <td>login_tenant_name</td>
    <td>yes</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td>The tenant name of the login user</td>
    </tr>
            <tr>
    <td>login_username</td>
    <td>yes</td>
    <td>admin</td>
        <td><ul></ul></td>
        <td>login username to authenticate to keystone</td>
    </tr>
            <tr>
    <td>min_disk</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The minimum disk space required to deploy this image</td>
    </tr>
            <tr>
    <td>min_ram</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The minimum ram required to deploy this image</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Name that has to be given to the image</td>
    </tr>
            <tr>
    <td>owner</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The owner of the image</td>
    </tr>
            <tr>
    <td>region_name</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Name of the region</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td>180</td>
        <td><ul></ul></td>
        <td>The time to wait for the image process to complete in seconds</td>
    </tr>
        </table>


.. note:: Requires glanceclient


.. note:: Requires keystoneclient


Examples
--------

.. raw:: html

    <br/>


::

    # Upload an image from an HTTP URL
    - glance_image: login_username=admin
                    login_password=passme
                    login_tenant_name=admin
                    name=cirros
                    container_format=bare
                    disk_format=qcow2
                    state=present
                    copy_from=http:launchpad.net/cirros/trunk/0.3.0/+download/cirros-0.3.0-x86_64-disk.img



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

