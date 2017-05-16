.. _rpm_key:


rpm_key - Adds or removes a gpg key from the rpm db
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Adds or removes (rpm --import) a gpg key to your rpm database.

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
    <td>key</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Key that will be modified. Can be a url, a file, or a keyid if the key already exists in the database.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Wheather the key will be imported or removed from the rpm db.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code> and the <code>key</code> is a url starting with https, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example action to import a key from a url
    - rpm_key: state=present key=http://apt.sw.be/RPM-GPG-KEY.dag.txt
    
    # Example action to import a key from a file
    - rpm_key: state=present key=/path/to/key.gpg
    
    # Example action to ensure a key is not present in the db
    - rpm_key: state=absent key=DEADB33F



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

