.. _svr4pkg:


svr4pkg - Manage Solaris SVR4 packages
++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages SVR4 packages on Solaris 10 and 11.
* These were the native packages on Solaris <= 10 and are available as a legacy feature in Solaris 11.
* Note that this is a very basic packaging system. It will not enforce dependencies on install or remove.




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
                <tr><td>category<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Install/Remove category instead of a single package.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Package name, e.g. <code>SUNWcsr</code></div>        </td></tr>
                <tr><td>proxy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>HTTP[s] proxy to be used if <code>src</code> is a URL.</div>        </td></tr>
                <tr><td>response_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the location of a response file to be used if package expects input on install. (added in Ansible 1.4)</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the location to install the package from. Required when <code>state=present</code>.</div><div>Can be any path acceptable to the <code>pkgadd</code> command's <code>-d</code> option. e.g.: <code>somefile.pkg</code>, <code>/dir/with/pkgs</code>, <code>http:/server/mypkgs.pkg</code>.</div><div>If using a file or directory, they must already be accessible by the host. See the <span class='module'>copy</span> module for a way to get them there.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to install (<code>present</code>), or remove (<code>absent</code>) a package.</div><div>If the package is to be installed, then <em>src</em> is required.</div><div>The SVR4 package system doesn't provide an upgrade operation. You need to uninstall the old, then install the new package.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>all</td>
        <td><ul><li>current</li><li>all</li></ul></td>
        <td><div>Whether to install the package only in the current zone, or install it into all zones.</div><div>The installation into all zones works only if you are working with the global zone.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install a package from an already copied file
    - svr4pkg:
        name: CSWcommon
        src: /tmp/cswpkgs.pkg
        state: present
    
    # Install a package directly from an http site
    - svr4pkg:
        name: CSWpkgutil
        src: 'http://get.opencsw.org/now'
        state: present
        zone: current
    
    # Install a package with a response file
    - svr4pkg:
        name: CSWggrep
        src: /tmp/third-party.pkg
        response_file: /tmp/ggrep.response
        state: present
    
    # Ensure that a package is not installed.
    - svr4pkg:
        name: SUNWgnome-sound-recorder
        state: absent
    
    # Ensure that a category is not installed.
    - svr4pkg:
        name: FIREFOX
        state: absent
        category: true





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
