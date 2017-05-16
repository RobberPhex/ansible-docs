.. _digital_ocean_sshkey:


digital_ocean_sshkey - Create/delete an SSH key in DigitalOcean
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Create/delete an SSH key.

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
    <td>api_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>DigitalOcean api key.</td>
    </tr>
            <tr>
    <td>client_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>DigitalOcean manager id.</td>
    </tr>
            <tr>
    <td>id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Numeric, the SSH key id you want to operate on.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>String, this is the name of an SSH key to create or destroy.</td>
    </tr>
            <tr>
    <td>ssh_pub_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The public SSH key you want to add to your account.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the target.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Ensure a SSH key is present
    # If a key matches this name, will return the ssh key id and changed = False
    # If no existing key matches this name, a new key is created, the ssh key id is returned and changed = False
    
    - digital_ocean_sshkey: >
          state=present
          name=my_ssh_key
          ssh_pub_key='ssh-rsa AAAA...'
          client_id=XXX
          api_key=XXX
    

.. note:: Two environment variables can be used, DO_CLIENT_ID and DO_API_KEY.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

