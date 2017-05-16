.. _crypttab:


crypttab - Encrypted Linux block devices
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

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
    <td>backing_device<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the underlying block device or file, or the UUID of a block-device prefixed with <em>UUID=</em></div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the encrypted block device as it appears in the <code>/etc/crypttab</code> file, or optionaly prefixed with <code>/dev/mapper/</code>, as it appears in the filesystem. <em>/dev/mapper/</em> will be stripped from <em>name</em>.</div></td></tr>
            <tr>
    <td>opts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A comma-delimited list of options. See <code>crypttab(5</code> ) for details.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>Encryption password, the path to a file containing the pasword, or 'none' or '-' if the password should be entered at boot.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/crypttab</td>
        <td><ul></ul></td>
        <td><div>Path to file to use instead of <code>/etc/crypttab</code>. This might be useful in a chroot environment.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>opts_present</li><li>opts_absent</li></ul></td>
        <td><div>Use <em>present</em> to add a line to <code>/etc/crypttab</code> or update it's definition if already present. Use <em>absent</em> to remove a line with matching <em>name</em>. Use <em>opts_present</em> to add options to those already present; options with different values will be updated. Use <em>opts_absent</em> to remove options from the existing set.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Set the options explicitly a device which must already exist
      crypttab: name=luks-home state=present opts=discard,cipher=aes-cbc-essiv:sha256
    
    - name: Add the 'discard' option to any existing options for all devices
      crypttab: name={{ item.device }} state=opts_present opts=discard
      with_items: ansible_mounts
      when: '/dev/mapper/luks-' in {{ item.device }}




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

