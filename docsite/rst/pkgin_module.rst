.. _pkgin:


pkgin - Package manager for SmartOS, NetBSD, et al.
+++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

The standard package manager for SmartOS, but also usable on NetBSD or any OS that uses ``pkgsrc``.  (Home: http://pkgin.net/)




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
        <td><div>Name of package to install/remove;</div><div>multiple names may be given, separated by commas</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Intended state of the package</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # install package foo
    - pkgin: name=foo state=present
    
    # remove package foo
    - pkgin: name=foo state=absent
    
    # remove packages foo and bar
    - pkgin: name=foo,bar state=absent


Notes
-----

.. note:: Known bug with pkgin < 0.8.0: if a package is removed and another package depends on it, the other package will be silently removed as well.  New to Ansible 1.9: check-mode support.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

