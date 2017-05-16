.. _gce_img:


gce_img - utilize GCE image resources
+++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9

This module can create and delete GCE private images from gzipped compressed tarball containing raw disk data or from existing detached disks in any zone. https://cloud.google.com/compute/docs/images

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
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>an optional description</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the name of the image to create or delete</td>
    </tr>
            <tr>
    <td>pem_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to the pem file associated with the service account email</td>
    </tr>
            <tr>
    <td>project_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>your GCE project ID</td>
    </tr>
            <tr>
    <td>service_account_email</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>service account email</td>
    </tr>
            <tr>
    <td>source</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the source disk or the Google Cloud Storage URI to create the image from</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>desired state of the image</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>no</td>
    <td>us-central1-a</td>
        <td><ul></ul></td>
        <td>the zone of the disk specified by source</td>
    </tr>
        </table>


.. note:: Requires libcloud


Examples
--------

.. raw:: html

    <br/>


::

    # Create an image named test-image from the disk 'test-disk' in zone us-central1-a.
    - gce_img:
        name: test-image
        source: test-disk
        zone: us-central1-a
        state: present
    
    # Create an image named test-image from a tarball in Google Cloud Storage.
    - gce_img:
        name: test-image
        source: https://storage.googleapis.com/bucket/path/to/image.tgz
        
    # Alternatively use the gs scheme
    - gce_img:
        name: test-image
        source: gs://bucket/path/to/image.tgz
    
    # Delete an image named test-image.
    - gce_img:
        name: test-image
        state: absent



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

