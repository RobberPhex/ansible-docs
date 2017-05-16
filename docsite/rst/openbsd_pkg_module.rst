.. _openbsd_pkg:


openbsd_pkg - Manage packages on OpenBSD.
+++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage packages on OpenBSD using the pkg tools.




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
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the package.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td><div><code>present</code> will make sure the package is installed. <code>latest</code> will make sure the latest version of the package is installed. <code>absent</code> will make sure the specified package is not installed.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Make sure nmap is installed
    - openbsd_pkg: name=nmap state=present
    
    # Make sure nmap is the latest version
    - openbsd_pkg: name=nmap state=latest
    
    # Make sure nmap is not installed
    - openbsd_pkg: name=nmap state=absent
    
    # Specify a pkg flavour with '--'
    - openbsd_pkg: name=vim--nox11 state=present
    
    # Specify the default flavour to avoid ambiguity errors
    - openbsd_pkg: name=vim-- state=present
    
    # Update all packages on the system
    - openbsd_pkg: name=* state=latest




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

