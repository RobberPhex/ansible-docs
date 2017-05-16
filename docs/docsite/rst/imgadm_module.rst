.. _imgadm:


imgadm - Manage SmartOS images
++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage SmartOS virtual machine images through imgadm(1M)


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6


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
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Force a given operation (where supported by imgadm(1M)).</div>        </td></tr>
                <tr><td>pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>zones</td>
        <td></td>
        <td><div>zpool to import to or delete images from.</div>        </td></tr>
                <tr><td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URI for the image source.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>deleted</li><li>imported</li><li>updated</li><li>vacuumed</li></ul></td>
        <td><div>State the object operated on should be in. <code>imported</code> is an alias for for <code>present</code> and <code>deleted</code> for <code>absent</code>. When set to <code>vacuumed</code> and <code>uuid</code> to <code>*</code>, it will remove all unused images.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>imgapi</td>
        <td><ul><li>imgapi</li><li>docker</li><li>dsapi</li></ul></td>
        <td><div>Type for image sources.</div>        </td></tr>
                <tr><td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Image UUID. Can either be a full UUID or <code>*</code> for all images.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Import an image
      imgadm:
        uuid: '70e3ae72-96b6-11e6-9056-9737fd4d0764'
        state: imported
    
    - name: Delete an image
      imgadm:
        uuid: '70e3ae72-96b6-11e6-9056-9737fd4d0764'
        state: deleted
    
    - name: Update all images
      imgadm:
        uuid: '*'
        state: updated
    
    - name: Update a single image
      imgadm:
        uuid: '70e3ae72-96b6-11e6-9056-9737fd4d0764'
        state: updated
    
    - name: Add a source
      imgadm:
        source: 'https://datasets.project-fifo.net'
        state: present
    
    - name: Add a Docker source
      imgadm:
        source: 'https://docker.io'
        type: docker
        state: present
    
    - name: Remove a source
      imgadm:
        source: 'https://docker.io'
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
        <td> source </td>
        <td> Source that is managed. </td>
        <td align=center> When not managing an image. </td>
        <td align=center> string </td>
        <td align=center> https://datasets.project-fifo.net </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the target, after execution. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> uuid </td>
        <td> UUID for an image operated on. </td>
        <td align=center> When not managing an image source. </td>
        <td align=center> string </td>
        <td align=center> 70e3ae72-96b6-11e6-9056-9737fd4d0764 </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
