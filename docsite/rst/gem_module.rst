.. _gem:


gem - Manage Ruby gems
++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage installation and uninstallation of Ruby gems.




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
    <td>build_flags<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Allow adding build flags for gem compilation</div></td></tr>
            <tr>
    <td>env_shebang<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul></ul></td>
        <td><div>Rewrite the shebang line on installed scripts to use /usr/bin/env.</div></td></tr>
            <tr>
    <td>executable<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Override the path to the gem executable</div></td></tr>
            <tr>
    <td>gem_source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to a local gem used as installation source.</div></td></tr>
            <tr>
    <td>include_dependencies<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to include dependencies or not.</div></td></tr>
            <tr>
    <td>include_doc<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul></ul></td>
        <td><div>Install with or without docs.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the gem to be managed.</div></td></tr>
            <tr>
    <td>pre_release<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul></ul></td>
        <td><div>Allow installation of pre-release versions of the gem.</div></td></tr>
            <tr>
    <td>repository<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The repository from which the gem will be installed</div></br>
        <div style="font-size: small;">aliases: source<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td><div>The desired state of the gem. <code>latest</code> ensures that the latest version is installed.</div></td></tr>
            <tr>
    <td>user_install<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td><div>Install gem in user's local gems cache or for all users</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Version of the gem to be installed/removed.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Installs version 1.0 of vagrant.
    - gem: name=vagrant version=1.0 state=present
    
    # Installs latest available version of rake.
    - gem: name=rake state=latest
    
    # Installs rake version 1.0 from a local gem on disk.
    - gem: name=rake gem_source=/path/to/gems/rake-1.0.gem state=present




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

