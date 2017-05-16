.. _crypttab:


crypttab - Encrypted Linux block devices
++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9

Control Linux encrypted block devices that are set up during system boot in ``/etc/crypttab``.

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
    <td>backing_device</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path to the underlying block device or file, or the UUID of a block-device prefixed with <em>UUID=</em></td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the encrypted block device as it appears in the <code>/etc/crypttab</code> file, or optionaly prefixed with <code>/dev/mapper/</code>, as it appears in the filesystem. <em>/dev/mapper/</em> will be stripped from <em>name</em>.</td>
    </tr>
            <tr>
    <td>opts</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A comma-delimited list of options. See <code>crypttab(5</code> ) for details.</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>Encryption password, the path to a file containing the pasword, or 'none' or '-' if the password should be entered at boot.</td>
    </tr>
            <tr>
    <td>path</td>
    <td>no</td>
    <td>/etc/crypttab</td>
        <td><ul></ul></td>
        <td>Path to file to use instead of <code>/etc/crypttab</code>. This might be useful in a chroot environment.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>opts_present</li><li>opts_absent</li></ul></td>
        <td>Use <em>present</em> to add a line to <code>/etc/crypttab</code> or update it's definition if already present. Use <em>absent</em> to remove a line with matching <em>name</em>. Use <em>opts_present</em> to add options to those already present; options with different values will be updated. Use <em>opts_absent</em> to remove options from the existing set.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    - name: Set the options explicitly a deivce which must already exist
      crypttab: name=luks-home state=present opts=discard,cipher=aes-cbc-essiv:sha256
    
    - name: Add the 'discard' option to any existing options for all devices
      crypttab: name={{ item.device }} state=opts_present opts=discard
      with_items: ansible_mounts
      when: '/dev/mapper/luks-' in {{ item.device }}



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

