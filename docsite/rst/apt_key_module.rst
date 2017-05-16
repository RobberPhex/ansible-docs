.. _apt_key:


apt_key - Add or remove an apt key
++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.0

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
    <td>data</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>keyfile contents</td>
    </tr>
            <tr>
    <td>file</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>keyfile path</td>
    </tr>
            <tr>
    <td>id</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>identifier of key</td>
    </tr>
            <tr>
    <td>keyring</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>path to specific keyring file in /etc/apt/trusted.gpg.d (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>keyserver</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>keyserver to retrieve key from. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td>used to specify if key is being added or revoked</td>
    </tr>
            <tr>
    <td>url</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>url to retrieve key from.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates for the target url will not be validated. This should only be used on personally controlled sites using self-signed certificates.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


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

.. note:: doesn't download the key unless it really needs it
.. note:: as a sanity check, downloaded key id must match the one specified
.. note:: best practice is to specify the key id and the url


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

