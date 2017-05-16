.. _pkg5:


pkg5 - Manages packages with the Solaris 11 Image Packaging System
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

IPS packages are the native packages in Solaris 11 and higher.




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
    <td>accept_licenses<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Accept any licences.</div></br>
        <div style="font-size: small;">aliases: accept_licences, accept<div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An FRMI of the package(s) to be installed/removed/updated.</div><div>Multiple packages may be specified, separated by <code>,</code>.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td><div>Whether to install (<em>present</em>, <em>latest</em>), or remove (<em>absent</em>) a package.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install Vim:
    - pkg5: name=editor/vim
    
    # Remove finger daemon:
    - pkg5: name=service/network/finger state=absent
    
    # Install several packages at once:
    - pkg5:
        name:
          - /file/gnu-findutils
          - /text/gnu-grep


Notes
-----

.. note:: The naming of IPS packages is explained at http://www.oracle.com/technetwork/articles/servers-storage-admin/ips-package-versioning-2232906.html.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

