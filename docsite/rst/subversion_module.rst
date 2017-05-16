.. _subversion:


subversion - Deploys a subversion repository.
+++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Deploy given repository URL / revision to dest. If dest exists, update to the specified revision, otherwise perform a checkout.




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
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Absolute path where the repository should be deployed.</div></td></tr>
            <tr>
    <td>executable<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to svn executable to use. If not supplied, the normal mechanism for resolving binary paths will be used.</div></td></tr>
            <tr>
    <td>export<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, do export instead of checkout/update.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, modified files will be discarded. If <code>no</code>, module will fail if it encounters modified files. Prior to 1.9 the default was `yes`.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>--password parameter passed to svn.</div></td></tr>
            <tr>
    <td>repo<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The subversion URL to the repository.</div></br>
        <div style="font-size: small;">aliases: name, repository<div></td></tr>
            <tr>
    <td>revision<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>HEAD</td>
        <td><ul></ul></td>
        <td><div>Specific revision to checkout.</div></br>
        <div style="font-size: small;">aliases: version<div></td></tr>
            <tr>
    <td>switch<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, do not call svn switch before update.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>--username parameter passed to svn.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Checkout subversion repository to specified folder.
    - subversion: repo=svn+ssh://an.example.org/path/to/repo dest=/src/checkout
    
    # Export subversion directory to folder
    - subversion: repo=svn+ssh://an.example.org/path/to/repo dest=/src/export export=True


Notes
-----

.. note:: Requires *svn* to be installed on the client.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

