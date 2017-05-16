.. _win_chocolatey:


win_chocolatey - Installs packages using chocolatey
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Installs packages using Chocolatey (http://chocolatey.org/).
* If Chocolatey is missing from the system, the module will install it.
* List of packages can be found at http://chocolatey.org/packages




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
                <tr><td>allow_empty_checksums<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Allow empty checksums to be used.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Forces install of the package (even if it already exists).</div><div>Using <code>force</code> will cause ansible to always report that a change was made.</div>        </td></tr>
                <tr><td>ignore_checksums<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ignore checksums altogether.</div>        </td></tr>
                <tr><td>ignore_dependencies<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ignore dependencies, only install/upgrade the package itself.</div>        </td></tr>
                <tr><td>install_args<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Arguments to pass to the native installer.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the package to be installed.</div>        </td></tr>
                <tr><td>params<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Parameters to pass to the package</div>        </td></tr>
                <tr><td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify source rather than using default chocolatey repository.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li><li>reinstalled</li></ul></td>
        <td><div>State of the package on the system.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>2700</td>
        <td></td>
        <td><div>The time to allow chocolatey to finish before timing out.</div></br>
    <div style="font-size: small;">aliases: execution_timeout<div>        </td></tr>
                <tr><td>upgrade<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If package is already installed it, try to upgrade to the latest version or to the specified version.</div><div>As of Ansible v2.3 this is deprecated, set parameter <code>state</code> to "latest" for the same result.</div>        </td></tr>
                <tr><td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specific version of the package to be installed.</div><div>Ignored when <code>state</code> is set to "absent".</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      # Install git
      win_chocolatey:
        name: git
        state: present
    
      # Upgrade installed packages
      win_chocolatey:
        name: all
        state: latest
    
      # Install notepadplusplus version 6.6
      win_chocolatey:
        name: notepadplusplus.install
        version: '6.6'
    
      # Install git from specified repository
      win_chocolatey:
        name: git
        source: https://someserver/api/v2/
    
      # Uninstall git
      win_chocolatey:
        name: git
        state: absent





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
