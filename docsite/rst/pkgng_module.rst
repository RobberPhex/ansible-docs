.. _pkgng:


pkgng - Package manager for FreeBSD >= 9.0
++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage binary packages for FreeBSD using 'pkgng' which is available in versions after 9.0.




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
    <td>annotation<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a comma-separated list of keyvalue-pairs of the form &lt;+/-/:&gt;&lt;key&gt;[=&lt;value&gt;]. A '+' denotes adding an annotation, a '-' denotes removing an annotation, and ':' denotes modifying an annotation. If setting or modifying annotations, a value must be provided.</div></td></tr>
            <tr>
    <td>cached<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>use local package base or try to fetch an updated one</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of package to install/remove</div></td></tr>
            <tr>
    <td>pkgsite<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>for pkgng versions before 1.1.4, specify packagesite to use for downloading packages, if not specified, use settings from /usr/local/etc/pkg.conf for newer pkgng versions, specify a the name of a repository configured in /usr/local/etc/pkg/repos</div></td></tr>
            <tr>
    <td>rootdir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>for pkgng versions 1.5 and later, pkg will install all packages within the specified root directory</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>state of the package</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install package foo
    - pkgng: name=foo state=present
    
    # Annotate package foo and bar
    - pkgng: name=foo,bar annotation=+test1=baz,-test2,:test3=foobar
    
    # Remove packages foo and bar 
    - pkgng: name=foo,bar state=absent


Notes
-----

.. note:: When using pkgsite, be careful that already in cache packages won't be downloaded again.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

