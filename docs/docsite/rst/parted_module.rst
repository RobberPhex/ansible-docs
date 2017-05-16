.. _parted:


parted - Configure block device partitions
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows configuring block device partition using the ``parted`` command line tool. For a full description of the fields and the options check the GNU parted manual.


Requirements (on host that executes module)
-------------------------------------------

  * This module requires parted version 1.8.3 and above.
  * If the version of parted is below 3.1, it requires a Linux version running the sysfs file system ``/sys/``.


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
                <tr><td>align<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>optimal</td>
        <td><ul><li>none</li><li>cylinder</li><li>minimal</li><li>optimal</li></ul></td>
        <td><div>Set alignment for newly created partitions.</div>        </td></tr>
                <tr><td>device<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The block device (disk) where to operate.</div>        </td></tr>
                <tr><td>flags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of the flags that has to be set on the partition.</div>        </td></tr>
                <tr><td>label<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>msdos</td>
        <td><ul><li>aix</li><li>amiga</li><li>bsd</li><li>dvh</li><li>gpt</li><li>loop</li><li>mac</li><li>msdos</li><li>pc98</li><li>sun</li><li></li></ul></td>
        <td><div>Creates a new disk label.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the name for the partition number (GPT, Mac, MIPS and PC98 only).</div>        </td></tr>
                <tr><td>number<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The number of the partition to work with or the number of the partition that will be created. Required when performing any action on the disk, except fetching information.</div>        </td></tr>
                <tr><td>part_end<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>100%</td>
        <td></td>
        <td><div>Where the partition will end as offset from the beginning of the disk, that is, the "distance" from the start of the disk. The distance can be specified with all the units supported by parted (except compat) and it is case sensitive. E.g. <code>10GiB</code>, <code>15%</code>.</div>        </td></tr>
                <tr><td>part_start<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0%</td>
        <td></td>
        <td><div>Where the partition will start as offset from the beginning of the disk, that is, the "distance" from the start of the disk. The distance can be specified with all the units supported by parted (except compat) and it is case sensitive. E.g. <code>10GiB</code>, <code>15%</code>.</div>        </td></tr>
                <tr><td>part_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>primary</li><li>extended</li><li>logical</li></ul></td>
        <td><div>Is one of 'primary', 'extended' or 'logical' and may be specified only with 'msdos' or 'dvh' partition tables. A name must be specified for a 'gpt' partition table. Neither part-type nor name may be used with a 'sun' partition table.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>info</td>
        <td><ul><li>present</li><li>absent</li><li>info</li></ul></td>
        <td><div>If to create or delete a partition. If set to <code>info</code> the module will only return the device information.</div>        </td></tr>
                <tr><td>unit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>KiB</td>
        <td><ul><li>s</li><li>B</li><li>KB</li><li>KiB</li><li>MB</li><li>MiB</li><li>GB</li><li>GiB</li><li>TB</li><li>TiB</li><li>%</li><li>cyl</li><li>chs</li><li>compact</li></ul></td>
        <td><div>Selects the current default unit that Parted will use to display locations and capacities on the disk and to interpret those given by the user if they are not suffixed by an unit. When fetching information about a disk, it is always recommended to specify a unit.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new primary partition
    - parted:
        device: /dev/sdb
        number: 1
        state: present
    
    # Remove partition number 1
    - parted:
        device: /dev/sdb
        number: 1
        state: absent
    
    # Create a new primary partition with a size of 1GiB
    - parted:
        device: /dev/sdb
        number: 1
        state: present
        part_end: 1GiB
    
    # Create a new primary partition for LVM
    - parted:
        device: /dev/sdb
        number: 2
        flags: [ lvm ]
        state: present
        part_start: 1GiB
    
    # Read device information (always use unit when probing)
    - parted: device=/dev/sdb unit=MiB
      register: sdb_info
    
    # Remove all partitions from disk
    - parted:
        device: /dev/sdb
        number: "{{ item.num }}"
        state: absent
      with_items:
       - "{{ sdb_info.partitions }}"

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
        <td> partition_info </td>
        <td> Current partition information </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - When fetching information about a new disk and when the version of parted installed on the system is before version 3.1, the module queries the kernel through ``/sys/`` to obtain disk information. In this case the units CHS and CYL are not supported.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
