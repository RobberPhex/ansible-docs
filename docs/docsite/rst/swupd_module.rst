.. _swupd:


swupd - Manages updates and bundles in ClearLinux systems.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages updates and bundles with the swupd bundle manager, which is used by the Clear Linux Project for Intel Architecture.




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
                <tr><td>contenturl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL pointing to the contents of available bundles. If not specified, the contents are retrieved from clearlinux.org.</div>        </td></tr>
                <tr><td>format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The format suffix for version file downloads. For example [1,2,3,staging,etc]. If not specified, the default format is used.</div>        </td></tr>
                <tr><td>manifest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The manifest contains information about the bundles at certaion version of the OS. Specify a Manifest version to verify against that version or leave unspecified to verify against the current version.</div></br>
    <div style="font-size: small;">aliases: release, version<div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the (I)bundle to install or remove.</div></br>
    <div style="font-size: small;">aliases: bundle<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicates the desired (I)bundle state. <code>present</code> ensures the bundle is installed while <code>absent</code> ensures the (I)bundle is not installed.</div>        </td></tr>
                <tr><td>update<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Updates the OS to the latest version.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Overrides both <em>contenturl</em> and <em>versionurl</em>.</div>        </td></tr>
                <tr><td>verify<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Verify content for OS version.</div>        </td></tr>
                <tr><td>versionurl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL for version string download.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Update the OS to the latest version
      swupd:
        update: yes
    
    - name: Installs the "foo" bundle
      swupd:
        name: foo
        state: present
    
    - name: Removes the "foo" bundle
      swupd:
        name: foo
        state: absent
    
    - name: Check integrity of filesystem
      swupd:
        verify: yes
    
    - name: Downgrade OS to release 12920
      swupd:
        verify: yes
        manifest: 12920

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
        <td> stderr </td>
        <td> stderr of swupd </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> stdout of swupd </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
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
