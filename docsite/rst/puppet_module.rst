.. _puppet:


puppet - Runs puppet
++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Runs *puppet* agent or apply in a reliable manner


Requirements
------------

  * puppet


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
    <td>environment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Puppet environment to be used.</div></td></tr>
            <tr>
    <td>facter_basename<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ansible</td>
        <td><ul></ul></td>
        <td><div>Basename of the facter output file</div></td></tr>
            <tr>
    <td>facts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A dict of values to pass in as persistent external facter facts</div></td></tr>
            <tr>
    <td>manifest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Path to the manifest file to run puppet apply on.</div></td></tr>
            <tr>
    <td>puppetmaster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The hostname of the puppetmaster to contact.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30m</td>
        <td><ul></ul></td>
        <td><div>How long to wait for <em>puppet</em> to finish.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Run puppet agent and fail if anything goes wrong
    - puppet
    
    # Run puppet and timeout in 5 minutes
    - puppet: timeout=5m
    
    # Run puppet using a different environment
    - puppet: environment=testing




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

