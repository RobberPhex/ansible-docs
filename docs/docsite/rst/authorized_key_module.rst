.. _authorized_key:


authorized_key - Adds or removes an SSH authorized key
++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Adds or removes SSH authorized keys for particular user accounts




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
                <tr><td>exclusive<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to remove all other non-specified keys from the authorized_keys file. Multiple keys can be specified in a single <code>key</code> string value by separating them by newlines.</div><div>This option is not loop aware, so if you use <code>with_</code> , it will be exclusive per iteration of the loop, if you want multiple keys in the file you need to pass them all to <code>key</code> in a single batch as mentioned above.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The SSH public key(s), as a string or (since 1.9) url (https://github.com/username.keys)</div>        </td></tr>
                <tr><td>key_options<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A string of ssh key options to be prepended to the key in the authorized_keys file</div>        </td></tr>
                <tr><td>manage_dir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether this module should manage the directory of the authorized key file.  If set, the module will create the directory, as well as set the owner and permissions of an existing directory. Be sure to set <code>manage_dir=no</code> if you are using an alternate directory for authorized_keys, as set with <code>path</code>, since you could lock yourself out of SSH access. See the example below.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>(homedir)+/.ssh/authorized_keys</td>
        <td></td>
        <td><div>Alternate path to the authorized_keys file</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the given key (with the given key_options) should or should not be in the file</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username on the remote host whose authorized_keys file will be modified</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This only applies if using a https url as the source of the keys. If set to <code>no</code>, the SSL certificates will not be validated.</div><div>This should only set to <code>no</code> used on personally controlled sites using self-signed certificates as it avoids verifying the source site.</div><div>Prior to 2.1 the code worked as if this was set to <code>yes</code>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Set authorized key took from file
      authorized_key:
        user: charlie
        state: present
        key: "{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
    
    - name: Set authorized key took from url
      authorized_key:
        user: charlie
        state: present
        key: https://github.com/charlie.keys
    
    - name: Set authorized key in alternate location
      authorized_key:
        user: charlie
        state: present
        key: "{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
        path: /etc/ssh/authorized_keys/charlie
        manage_dir: False
    
    - name: Set up multiple authorized keys
      authorized_key:
        user: deploy
        state: present
        key: '{{ item }}'
      with_file:
        - public_keys/doe-jane
        - public_keys/doe-john
    
    - name: Set authorized key defining key options
      authorized_key:
        user: charlie
        state: present
        key: "{{ lookup('file', '/home/charlie/.ssh/id_rsa.pub') }}"
        key_options: 'no-port-forwarding,from="10.0.1.1"'
    
    - name: Set authorized key without validating the TLS/SSL certificates
      authorized_key:
        user: charlie
        state: present
        key: https://github.com/user.keys
        validate_certs: False
    
    - name: Set authorized key, removing all the authorized key already set
      authorized_key:
        user: root
        key: '{{ item }}'
        state: present
        exclusive: True
      with_file:
        - public_keys/doe-jane
    
    - name: Set authorized key for user ubuntu copying it from current user
      authorized_key:
        user: ubuntu
        state: present
        key: "{{ lookup('file', lookup('env','HOME') + '/.ssh/id_rsa.pub') }}"

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> exclusive </td>
        <td> If the key has been forced to be exclusive or not. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> key_option </td>
        <td> Key options related to the key. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> state </td>
        <td> Whether the given key (with the given key_options) should or should not be in the file </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> user </td>
        <td> The username on the remote host whose authorized_keys file will be modified </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> key </td>
        <td> The key that the module was running against. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> https://github.com/user.keys </td>
    </tr>
            <tr>
        <td> path </td>
        <td> Alternate path to the authorized_keys file </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> unique </td>
        <td> Whether the key is unique </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> validate_certs </td>
        <td> This only applies if using a https url as the source of the keys. If set to C(no), the SSL certificates will not be validated. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> keyfile </td>
        <td> Path for authorzied key file. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> manage_dir </td>
        <td> Whether this module managed the directory of the authorized key file. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
