.. _authorized_key:


authorized_key - Adds or removes an SSH authorized key
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Adds or removes authorized keys for particular user accounts

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
        <td>The SSH public key, as a string</td>
    </tr>
            <tr>
    <td>key_options</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A string of ssh key options to be prepended to the key in the authorized_keys file (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>manage_dir</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether this module should manage the directory of the authorized key file.  If set, the module will create the directory, as well as set the owner and permissions of an existing directory. Be sure to set <code>manage_dir=no</code> if you are using an alternate directory for authorized_keys, as set with <code>path</code>, since you could lock yourself out of SSH access. See the example below. (added in Ansible 1.2)</td>
    </tr>
            <tr>
    <td>path</td>
    <td>no</td>
    <td>(homedir)+/.ssh/authorized_keys</td>
        <td><ul></ul></td>
        <td>Alternate path to the authorized_keys file (added in Ansible 1.2)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether the given key (with the given key_options) should or should not be in the file</td>
    </tr>
            <tr>
    <td>user</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The username on the remote host whose authorized_keys file will be modified</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example using key data from a local file on the management machine
    - authorized_key: user=charlie key="{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
    
    # Using alternate directory locations:
    - authorized_key: user=charlie
                      key="{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
                      path='/etc/ssh/authorized_keys/charlie'
                      manage_dir=no
    
    # Using with_file
    - name: Set up authorized_keys for the deploy user
      authorized_key: user=deploy
                      key="{{ item }}"
      with_file:
        - public_keys/doe-jane
        - public_keys/doe-john
    
    # Using key_options:
    - authorized_key: user=charlie
                      key="{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
                      key_options='no-port-forwarding,host="10.0.1.1"'



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

