.. _gce_tag:


gce_tag - add or remove tag(s) to/from GCE instances
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module can add or remove tags https://cloud.google.com/compute/docs/label-or-tag-resources#tags to/from GCE instances.  Use 'instance_pattern' to update multiple instances in a specify zone


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * apache-libcloud >= 0.17.0


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
                <tr><td>instance_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the GCE instance to add/remove tags.  Required if instance_pattern is not specified.</div>        </td></tr>
                <tr><td>instance_pattern<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The pattern of GCE instance names to match for adding/removing tags.  Full-Python regex is supported. See <a href='https://docs.python.org/2/library/re.html'>https://docs.python.org/2/library/re.html</a> for details. If instance_name is not specified, this field is required.</div>        </td></tr>
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
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>desired state of the tags</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>comma-separated list of tags to add or remove</div>        </td></tr>
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

    # Add tags 'http-server', 'https-server', 'staging' to instance name 'staging-server' in zone us-central1-a.
    - gce_tag:
        instance_name: staging-server
        tags: http-server,https-server,staging
        zone: us-central1-a
        state: present
    
    # Remove tags 'foo', 'bar' from instance 'test-server' in default zone (us-central1-a)
    - gce_tag:
        instance_name: test-server
        tags: foo,bar
        state: absent
    
    # Add tags 'foo', 'bar' to instances in zone that match pattern
    - gce_tag:
        instance_pattern: test-server-*
        tags: foo,bar
        zone: us-central1-a
        state: present
    


Notes
-----

.. note::
    - Either *instance_name* or *instance_pattern* is required.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
