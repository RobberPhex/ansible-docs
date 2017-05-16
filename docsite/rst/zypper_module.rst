.. _zypper:


zypper - Manage packages on SUSE and openSUSE
+++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage packages on SUSE and openSUSE using the zypper and rpm tools.


Requirements
------------

  * zypper
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
            <tr>
    <td>disable_gpg_check<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to disable to GPG signature checking of the package signature being installed. Has an effect only if state is <em>present</em> or <em>latest</em>.</div></td></tr>
            <tr>
    <td>disable_recommends<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Corresponds to the <code>--no-recommends</code> option for <em>zypper</em>. Default behavior (<code>yes</code>) modifies zypper's default behavior; <code>no</code> does install recommended packages.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>package name or package specifier with version <code>name</code> or <code>name-1.0</code>. You can also pass a url or a local path to a rpm file.</div></br>
        <div style="font-size: small;">aliases: pkg<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td><div><code>present</code> will make sure the package is installed. <code>latest</code>  will make sure the latest version of the package is installed. <code>absent</code>  will make sure the specified package is not installed.</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>package</td>
        <td><ul><li>package</li><li>patch</li><li>pattern</li><li>product</li><li>srcpackage</li></ul></td>
        <td><div>The type of package to be operated on.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install "nmap"
    - zypper: name=nmap state=present
    
    # Install apache2 with recommended packages
    - zypper: name=apache2 state=present disable_recommends=no
    
    # Remove the "nmap" package
    - zypper: name=nmap state=absent
    
    # Install the nginx rpm from a remote repo
    - zypper: name=http://nginx.org/packages/sles/12/x86_64/RPMS/nginx-1.8.0-1.sles12.ngx.x86_64.rpm state=present
    
    # Install local rpm file
    - zypper: name=/tmp/fancy-software.rpm state=present




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

