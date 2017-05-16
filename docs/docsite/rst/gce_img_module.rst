.. _gce_img:


gce_img - utilize GCE image resources
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module can create and delete GCE private images from gzipped compressed tarball containing raw disk data or from existing detached disks in any zone. https://cloud.google.com/compute/docs/images


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * apache-libcloud


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
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>an optional description</div>        </td></tr>
                <tr><td>family<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>an optional family name</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the name of the image to create or delete</div>        </td></tr>
                <tr><td>pem_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>path to the pem file associated with the service account email</div>        </td></tr>
                <tr><td>project_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>your GCE project ID</div>        </td></tr>
                <tr><td>service_account_email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>service account email</div>        </td></tr>
                <tr><td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the source disk or the Google Cloud Storage URI to create the image from</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>desired state of the image</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>180</td>
        <td></td>
        <td><div>timeout for the operation</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>us-central1-a</td>
        <td></td>
        <td><div>the zone of the disk specified by source</div>        </td></tr>
        </table>
    </br>



Examples
--------

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





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
