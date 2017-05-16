.. _homebrew_cask:


homebrew_cask - Install/uninstall homebrew casks.
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages Homebrew casks.


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
            <tr>
    <td>install_options<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>options flags to install a package</div></br>
        <div style="font-size: small;">aliases: options<div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of cask to install/remove</div></br>
        <div style="font-size: small;">aliases: pkg, package, cask<div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/usr/local/bin</td>
        <td><ul></ul></td>
        <td><div>':' separated list of paths to search for 'brew' executable.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>state of the cask</div></td></tr>
            <tr>
    <td>update_homebrew<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>update homebrew itself first. Note that <code>brew cask update</code> is a synonym for <code>brew update</code>.</div></br>
        <div style="font-size: small;">aliases: update-brew<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - homebrew_cask: name=alfred state=present
    - homebrew_cask: name=alfred state=absent
    - homebrew_cask: name=alfred state=present install_options="appdir=/Applications"
    - homebrew_cask: name=alfred state=present install_options="debug,appdir=/Applications"
    - homebrew_cask: name=alfred state=absent install_options="force"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

