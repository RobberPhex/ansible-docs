.. _pkg5_publisher:


pkg5_publisher - Manages Solaris 11 Image Packaging System publishers
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

IPS packages are the native packages in Solaris 11 and higher.
This modules will configure which publishers a client will download IPS packages from.




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
    <td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Is the repository enabled or disabled?</div></td></tr>
            <tr>
    <td>mirror<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A path or URL to the repository mirror.</div><div>Multiple values may be provided.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The publisher's name.</div></br>
        <div style="font-size: small;">aliases: publisher<div></td></tr>
            <tr>
    <td>origin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A path or URL to the repository.</div><div>Multiple values may be provided.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to ensure that a publisher is present or absent.</div></td></tr>
            <tr>
    <td>sticky<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Packages installed from a sticky repository can only receive updates from that repository.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Fetch packages for the solaris publisher direct from Oracle:
    - pkg5_publisher: name=solaris sticky=true origin=https://pkg.oracle.com/solaris/support/
    
    # Configure a publisher for locally-produced packages:
    - pkg5_publisher: name=site origin=https://pkg.example.com/site/




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

