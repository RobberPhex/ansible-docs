.. _lxd_profile:


lxd_profile - Manage LXD profiles
+++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Management of LXD profiles




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
    <td>cert_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>"{}/.config/lxc/client.crt" .format(os.environ["HOME"])</td>
        <td><ul></ul></td>
        <td><div>The client certificate file path.</div></td></tr>
            <tr>
    <td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The config for the container (e.g. {"limits.memory": "4GB"}). See <a href='https://github.com/lxc/lxd/blob/master/doc/rest-api.md#patch-3'>https://github.com/lxc/lxd/blob/master/doc/rest-api.md#patch-3</a></div><div>If the profile already exists and its "config" value in metadata obtained from GET /1.0/profiles/&lt;name&gt; <a href='https://github.com/lxc/lxd/blob/master/doc/rest-api.md#get-19'>https://github.com/lxc/lxd/blob/master/doc/rest-api.md#get-19</a> are different, they this module tries to apply the configurations.</div><div>Not all config values are supported to apply the existing profile. Maybe you need to delete and recreate a profile.</div></td></tr>
            <tr>
    <td>devices<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The devices for the profile (e.g. {"rootfs": {"path": "/dev/kvm", "type": "unix-char"}). See <a href='https://github.com/lxc/lxd/blob/master/doc/rest-api.md#patch-3'>https://github.com/lxc/lxd/blob/master/doc/rest-api.md#patch-3</a></div></td></tr>
            <tr>
    <td>key_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>"{}/.config/lxc/client.key" .format(os.environ["HOME"])</td>
        <td><ul></ul></td>
        <td><div>The client certificate key file path.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of a profile.</div></td></tr>
            <tr>
    <td>new_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A new name of a profile.</div><div>If this parameter is specified a profile will be renamed to this name. See <a href='https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-11'>https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-11</a></div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Define the state of a profile.</div></td></tr>
            <tr>
    <td>trust_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The client trusted password.</div><div>You need to set this password on the LXD server before running this module using the following command. lxc config set core.trust_password &lt;some random password&gt; See <a href='https://www.stgraber.org/2016/04/18/lxd-api-direct-interaction/'>https://www.stgraber.org/2016/04/18/lxd-api-direct-interaction/</a></div><div>If trust_password is set, this module send a request for authentication before sending any requests.</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>unix:/var/lib/lxd/unix.socket</td>
        <td><ul></ul></td>
        <td><div>The unix domain socket path or the https URL for the LXD server.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # An example for creating a profile
    - hosts: localhost
      connection: local
      tasks:
        - name: Create a profile
          lxd_profile:
            name: macvlan
            state: present
            config: {}
            description: 'my macvlan profile'
            devices:
              eth0:
                nictype: macvlan
                parent: br0
                type: nic
    
    # An example for creating a profile via http connection
    - hosts: localhost
      connection: local
      tasks:
      - name: create macvlan profile
        lxd_profile:
          url: https://127.0.0.1:8443
          # These cert_file and key_file values are equal to the default values.
          #cert_file: "{{ lookup('env', 'HOME') }}/.config/lxc/client.crt"
          #key_file: "{{ lookup('env', 'HOME') }}/.config/lxc/client.key"
          trust_password: mypassword
          name: macvlan
          state: present
          config: {}
          description: 'my macvlan profile'
          devices:
            eth0:
              nictype: macvlan
              parent: br0
              type: nic
    
    # An example for deleting a profile
    - hosts: localhost
      connection: local
      tasks:
        - name: Delete a profile
          lxd_profile:
            name: macvlan
            state: absent
    
    # An example for renaming a profile
    - hosts: localhost
      connection: local
      tasks:
        - name: Rename a profile
          lxd_profile:
            name: macvlan
            new_name: macvlan2
            state: present

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
        <td> old_state </td>
        <td> The old state of the profile </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> absent </td>
    </tr>
            <tr>
        <td> logs </td>
        <td> The logs of requests and responses. </td>
        <td align=center> when ansible-playbook is invoked with -vvvv. </td>
        <td align=center> list </td>
        <td align=center> (too long to be placed here) </td>
    </tr>
            <tr>
        <td> actions </td>
        <td> List of actions performed for the profile. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> ["create"] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Profiles must have a unique name. If you attempt to create a profile with a name that already existed in the users namespace the module will simply return as "unchanged".


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

