.. _digital_ocean:


digital_ocean - Create/delete a droplet/SSH_key in DigitalOcean
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Create/delete a droplet in DigitalOcean and optionally wait for it to be 'running', or deploy an SSH key.

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
    <td>backups_enabled</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Optional, Boolean, enables backups for your droplet. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>client_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>DigitalOcean manager id.</td>
    </tr>
            <tr>
    <td>command</td>
    <td>no</td>
    <td>droplet</td>
        <td><ul><li>droplet</li><li>ssh</li></ul></td>
        <td>Which target you want to operate on.</td>
    </tr>
            <tr>
    <td>id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Numeric, the droplet id you want to operate on.</td>
    </tr>
            <tr>
    <td>image_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Numeric, this is the id of the image you would like the droplet created with.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>String, this is the name of the droplet - must be formatted by hostname rules, or the name of a SSH key.</td>
    </tr>
            <tr>
    <td>private_networking</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Bool, add an additional, private network interface to droplet for inter-droplet communication. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>region_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Numeric, this is the id of the region you would like your server to be created in.</td>
    </tr>
            <tr>
    <td>size_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Numeric, this is the id of the size you would like the droplet created with.</td>
    </tr>
            <tr>
    <td>ssh_key_ids</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optional, comma separated list of ssh_key_ids that you would like to be added to the server.</td>
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
        <td><ul><li>present</li><li>active</li><li>absent</li><li>deleted</li></ul></td>
        <td>Indicate desired state of the target.</td>
    </tr>
            <tr>
    <td>unique_name</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Bool, require unique hostnames.  By default, DigitalOcean allows multiple hosts with the same name.  Setting this to "yes" allows only one host per name.  Useful for idempotence. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>virtio</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Bool, turn on virtio driver in droplet for improved network and storage I/O. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Wait for the droplet to be in state 'running' before returning.  If wait is "no" an ip_address may not be returned.</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>How long before wait gives up, in seconds.</td>
    </tr>
        </table>


.. note:: Requires dopy


Examples
--------

.. raw:: html

    <br/>


::

    # Ensure a SSH key is present
    # If a key matches this name, will return the ssh key id and changed = False
    # If no existing key matches this name, a new key is created, the ssh key id is returned and changed = False
    
    - digital_ocean: >
          state=present
          command=ssh
          name=my_ssh_key
          ssh_pub_key='ssh-rsa AAAA...'
          client_id=XXX
          api_key=XXX
    
    # Create a new Droplet
    # Will return the droplet details including the droplet id (used for idempotence)
    
    - digital_ocean: >
          state=present
          command=droplet
          name=mydroplet
          client_id=XXX
          api_key=XXX
          size_id=1
          region_id=2
          image_id=3
          wait_timeout=500
      register: my_droplet
    - debug: msg="ID is {{ my_droplet.droplet.id }}"
    - debug: msg="IP is {{ my_droplet.droplet.ip_address }}"
    
    # Ensure a droplet is present
    # If droplet id already exist, will return the droplet details and changed = False
    # If no droplet matches the id, a new droplet will be created and the droplet details (including the new id) are returned, changed = True.
    
    - digital_ocean: >
          state=present
          command=droplet
          id=123
          name=mydroplet
          client_id=XXX
          api_key=XXX
          size_id=1
          region_id=2
          image_id=3
          wait_timeout=500
    
    # Create a droplet with ssh key
    # The ssh key id can be passed as argument at the creation of a droplet (see ssh_key_ids).
    # Several keys can be added to ssh_key_ids as id1,id2,id3
    # The keys are used to connect as root to the droplet.
    
    - digital_ocean: >
          state=present
          ssh_key_ids=id1,id2
          name=mydroplet
          client_id=XXX
          api_key=XXX
          size_id=1
          region_id=2
          image_id=3

.. note:: Two environment variables can be used, DO_CLIENT_ID and DO_API_KEY.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

