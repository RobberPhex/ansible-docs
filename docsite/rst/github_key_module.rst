.. _github_key:


github_key - Manage GitHub access keys.
+++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates, removes, or updates GitHub access keys.




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
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The default is <code>yes</code>, which will replace the existing remote key if it's different than <code>pubkey</code>. If <code>no</code>, the key will only be set if no key with the given <code>name</code> exists.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>SSH key name</div></td></tr>
            <tr>
    <td>pubkey<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>SSH public key value. Required when <code>state=present</code>.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to remove a key, ensure that it exists, or update its value.</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>GitHub Access Token with permission to list and create public keys.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Read SSH public key to authorize
      shell: cat /home/foo/.ssh/id_rsa.pub
      register: ssh_pub_key
    
    - name: Authorize key with GitHub
      local_action:
        module: github_key
        name: 'Access Key for Some Machine'
        token: '{{github_access_token}}'
        pubkey: '{{ssh_pub_key.stdout}}'

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
        <td> matching_keys </td>
        <td> An array of keys matching the specified name. Only present on state=present </td>
        <td align=center> When state=present </td>
        <td align=center> list </td>
        <td align=center> [{'url': 'http://example.com/github key', 'read_only': False, 'created_at': 'YYYY-MM-DDTHH:MM:SZ', 'id': 0, 'key': 'BASE64 encoded key'}] </td>
    </tr>
            <tr>
        <td> deleted_keys </td>
        <td> An array of key objects that were deleted. Only present on state=absent </td>
        <td align=center> When state=absent </td>
        <td align=center> list </td>
        <td align=center> [{'url': 'http://example.com/github key', 'read_only': False, 'created_at': 'YYYY-MM-DDTHH:MM:SZ', 'id': 0, 'key': 'BASE64 encoded key'}] </td>
    </tr>
            <tr>
        <td> key </td>
        <td> Metadata about the key just created. Only present on state=present </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'url': 'http://example.com/github key', 'read_only': False, 'created_at': 'YYYY-MM-DDTHH:MM:SZ', 'id': 0, 'key': 'BASE64 encoded key'} </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

