.. _apt_key:


apt_key - Add or remove an apt key
++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove an *apt* key, optionally downloading it




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
    <td>data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>keyfile contents</div></td></tr>
            <tr>
    <td>file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>keyfile path</div></td></tr>
            <tr>
    <td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>identifier of key. Including this allows check mode to correctly report the changed state.</div></td></tr>
            <tr>
    <td>keyring<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>path to specific keyring file in /etc/apt/trusted.gpg.d</div></td></tr>
            <tr>
    <td>keyserver<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>keyserver to retrieve key from.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>used to specify if key is being added or revoked</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>url to retrieve key from.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates for the target url will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add an apt key by id from a keyserver
    - apt_key: keyserver=keyserver.ubuntu.com id=36A1D7869245C8950F966E92D8576A8BA88D21E9
    
    # Add an Apt signing key, uses whichever key is at the URL
    - apt_key: url=https://ftp-master.debian.org/keys/archive-key-6.0.asc state=present
    
    # Add an Apt signing key, will not download if present
    - apt_key: id=473041FA url=https://ftp-master.debian.org/keys/archive-key-6.0.asc state=present
    
    # Remove an Apt signing key, uses whichever key is at the URL
    - apt_key: url=https://ftp-master.debian.org/keys/archive-key-6.0.asc state=absent
    
    # Remove a Apt specific signing key, leading 0x is valid
    - apt_key: id=0x473041FA state=absent
    
    # Add a key from a file on the Ansible server
    - apt_key: data="{{ lookup('file', 'apt.gpg') }}" state=present
    
    # Add an Apt signing key to a specific keyring file
    - apt_key: id=473041FA url=https://ftp-master.debian.org/keys/archive-key-6.0.asc keyring=/etc/apt/trusted.gpg.d/debian.gpg state=present


Notes
-----

.. note:: doesn't download the key unless it really needs it
.. note:: as a sanity check, downloaded key id must match the one specified
.. note:: best practice is to specify the key id and the url


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

