.. _zypper:


zypper - Manage packages on SUSE and openSUSE
+++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage packages on SUSE and openSUSE using the zypper and rpm tools.


Requirements (on host that executes module)
-------------------------------------------

  * zypper >= 1.0  # included in openSuSE >= 11.1 or SuSE Linux Enterprise Server/Desktop >= 11.0
  * python-xml
  * rpm


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
                <tr><td>disable_gpg_check<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to disable to GPG signature checking of the package signature being installed. Has an effect only if state is <em>present</em> or <em>latest</em>.</div>        </td></tr>
                <tr><td>disable_recommends<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Corresponds to the <code>--no-recommends</code> option for <em>zypper</em>. Default behavior (<code>yes</code>) modifies zypper's default behavior; <code>no</code> does install recommended packages.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Adds <code>--force</code> option to <em>zypper</em>. Allows to downgrade packages and change vendor or architecture.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Package name <code>name</code> or package specifier.</div><div>Can include a version like <code>name=1.0</code>, <code>name&gt;3.4</code> or <code>name&lt;=2.7</code>. If a version is given, <code>oldpackage</code> is implied and zypper is allowed to update the package within the version range given.</div><div>You can also pass a url or a local path to a rpm file.</div><div>When using state=latest, this can be '*', which updates all installed packages.</div></br>
    <div style="font-size: small;">aliases: pkg<div>        </td></tr>
                <tr><td>oldpackage<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Adds <code>--oldpackage</code> option to <em>zypper</em>. Allows to downgrade packages with less side-effects than force. This is implied as soon as a version is specified as part of the package name.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td><div><code>present</code> will make sure the package is installed. <code>latest</code>  will make sure the latest version of the package is installed. <code>absent</code>  will make sure the specified package is not installed.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>package</td>
        <td><ul><li>package</li><li>patch</li><li>pattern</li><li>product</li><li>srcpackage</li><li>application</li></ul></td>
        <td><div>The type of package to be operated on.</div>        </td></tr>
                <tr><td>update_cache<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Run the equivalent of <code>zypper refresh</code> before the operation. Disabled in check mode.</div></br>
    <div style="font-size: small;">aliases: refresh<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install "nmap"
    - zypper:
        name: nmap
        state: present
    
    # Install apache2 with recommended packages
    - zypper:
        name: apache2
        state: present
        disable_recommends: no
    
    # Apply a given patch
    - zypper:
        name: openSUSE-2016-128
        state: present
        type: patch
    
    # Remove the "nmap" package
    - zypper:
        name: nmap
        state: absent
    
    # Install the nginx rpm from a remote repo
    - zypper:
        name: 'http://nginx.org/packages/sles/12/x86_64/RPMS/nginx-1.8.0-1.sles12.ngx.x86_64.rpm'
        state: present
    
    # Install local rpm file
    - zypper:
        name: /tmp/fancy-software.rpm
        state: present
    
    # Update all packages
    - zypper:
        name: '*'
        state: latest
    
    # Apply all available patches
    - zypper:
        name: '*'
        state: latest
        type: patch
    
    # Refresh repositories and update package "openssl"
    - zypper:
        name: openssl
        state: present
        update_cache: yes
    
    # Install specific version (possible comparisons: <, >, <=, >=, =)
    - zypper:
        name: 'docker>=1.10'
        state: present
    
    # Wait 20 seconds to acquire the lock before failing
    - zypper:
        name: mosh
        state: present
      environment:
        ZYPP_LOCK_TIMEOUT: 20





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
