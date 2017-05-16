.. _gce_tag:


gce_tag - add or remove tag(s) to/from GCE instance
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module can add or remove tags https://cloud.google.com/compute/docs/instances/#tags to/from GCE instance.


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
            <tr>
    <td>instance_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the name of the GCE instance to add/remove tags</div></td></tr>
            <tr>
    <td>pem_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to the pem file associated with the service account email</div></td></tr>
            <tr>
    <td>project_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>your GCE project ID</div></td></tr>
            <tr>
    <td>service_account_email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>service account email</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>desired state of the tags</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>comma-separated list of tags to add or remove</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>us-central1-a</td>
        <td><ul></ul></td>
        <td><div>the zone of the disk specified by source</div></td></tr>
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
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

