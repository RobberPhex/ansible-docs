.. _authorized_key:


authorized_key - Adds or removes an SSH authorized key
++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Adds or removes SSH authorized keys for particular user accounts




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
    <td>exclusive<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to remove all other non-specified keys from the authorized_keys file. Multiple keys can be specified in a single <code>key</code> string value by separating them by newlines.</div><div>This option is not loop aware, so if you use <code>with_</code> , it will be exclusive per iteration of the loop, if you want multiple keys in the file you need to pass them all to <code>key</code> in a single batch as mentioned above.</div></td></tr>
            <tr>
    <td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The SSH public key(s), as a string or (since 1.9) url (https://github.com/username.keys)</div></td></tr>
            <tr>
    <td>key_options<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A string of ssh key options to be prepended to the key in the authorized_keys file</div></td></tr>
            <tr>
    <td>manage_dir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether this module should manage the directory of the authorized key file.  If set, the module will create the directory, as well as set the owner and permissions of an existing directory. Be sure to set <code>manage_dir=no</code> if you are using an alternate directory for authorized_keys, as set with <code>path</code>, since you could lock yourself out of SSH access. See the example below.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>(homedir)+/.ssh/authorized_keys</td>
        <td><ul></ul></td>
        <td><div>Alternate path to the authorized_keys file</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the given key (with the given key_options) should or should not be in the file</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username on the remote host whose authorized_keys file will be modified</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This only applies if using a https url as the source of the keys. If set to <code>no</code>, the SSL certificates will not be validated.</div><div>This should only set to <code>no</code> used on personally controlled sites using self-signed certificates as it avoids verifying the source site.</div><div>Prior to 2.1 the code worked as if this was set to <code>yes</code>.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example using key data from a local file on the management machine
    - authorized_key: user=charlie key="{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
    
    # Using github url as key source
    - authorized_key: user=charlie key=https://github.com/charlie.keys
    
    # Using alternate directory locations:
    - authorized_key:
        user: charlie
        key: "{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
        path: '/etc/ssh/authorized_keys/charlie'
        manage_dir: no
    
    # Using with_file
    - name: Set up authorized_keys for the deploy user
      authorized_key: user=deploy key="{{ item }}"
      with_file:
        - public_keys/doe-jane
        - public_keys/doe-john
    
    # Using key_options:
    - authorized_key:
        user: charlie
        key:  "{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
        key_options: 'no-port-forwarding,from="10.0.1.1"'
    
    # Using validate_certs:
    - authorized_key: user=charlie key=https://github.com/user.keys validate_certs=no
    
    # Set up authorized_keys exclusively with one key
    - authorized_key: user=root key="{{ item }}" state=present exclusive=yes
      with_file:
        - public_keys/doe-jane
    
    # Copies the key from the user who is running ansible to the remote machine user ubuntu
    - authorized_key: user=ubuntu key="{{ lookup('file', lookup('env','HOME') + '/.ssh/id_rsa.pub') }}"
      become: yes
    




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

