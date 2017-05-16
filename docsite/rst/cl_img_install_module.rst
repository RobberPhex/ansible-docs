.. _cl_img_install:


cl_img_install - Install a different Cumulus Linux version.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

install a different version of Cumulus Linux in the inactive slot. For more details go the Image Management User Guide @ http://docs.cumulusnetworks.com/


Requirements (on host that executes module)
-------------------------------------------

  * Cumulus Linux OS


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
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>full path to the Cumulus Linux binary image. Can be a local path, http or https URL. If the code version is in the name of the file, the module will assume this is the version of code you wish to install.</div></td></tr>
            <tr>
    <td>switch_slot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Switch slots after installing the image. To run the installed code, reboot the switch</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>inform the module of the exact version one is installing. This overrides the automatic check of version in the file name. For example, if the binary file name is called CumulusLinux-2.2.3.bin, and version is set to '2.5.0', then the module will assume it is installing '2.5.0' not '2.2.3'. If version is not included, then the module will assume '2.2.3' is the version to install.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    Example playbook entries using the cl_img_install module
    
    ## Download and install the image from a webserver.
    
       - name: install image using using http url. Switch slots so the subsequent
         will load the new version
          cl_img_install: version=2.0.1
              src='http://10.1.1.1/CumulusLinux-2.0.1.bin'
              switch_slot=yes
    
    ## Copy the software from the ansible server to the switch.
    ## The module will get the code version from the filename
    ## The code will be installed in the alternate slot but the slot will not be primary
    ## A subsequent reload will not run the new code
    
        - name: download cumulus linux to local system
          get_url: src=ftp://cumuluslinux.bin dest=/root/CumulusLinux-2.0.1.bin
    
        - name: install image from local filesystem. Get version from the filename
          cl_img_install:  src='/root/CumulusLinux-2.0.1.bin'
    
    
    ## If the image name has been changed from the original name, use the `version` option
    ## to inform the module exactly what code version is been installed
    
        - name: download cumulus linux to local system
          get_url: src=ftp://CumulusLinux-2.0.1.bin dest=/root/image.bin
    
        - name: install image and switch slots. only reboot needed
          cl_img_install: version=2.0.1 src=/root/image.bin switch_slot=yes'

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
        <td> msg </td>
        <td> human-readable report of success or failure </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> interface bond0 config updated </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> whether the interface was changed </td>
        <td align=center> changed </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

