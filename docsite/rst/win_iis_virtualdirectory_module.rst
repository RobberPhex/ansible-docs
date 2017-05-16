.. _win_iis_virtualdirectory:


win_iis_virtualdirectory - Configures a virtual directory in IIS.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates, Removes and configures a virtual directory in IIS.




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
    <td>application<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The application under which the virtual directory is created or exists.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the virtual directory to create or remove</div></td></tr>
            <tr>
    <td>physical_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The physical path to the folder in which the new virtual directory is created. The specified folder must already exist.</div></td></tr>
            <tr>
    <td>site<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The site name under which the virtual directory is created or exists.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Whether to add or remove the specified virtual directory</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # This creates a virtual directory if it doesn't exist.
    $ ansible -i hosts -m win_iis_virtualdirectory -a "name='somedirectory' site=somesite state=present physical_path=c:\virtualdirectory\some" host
    
    # This removes a virtual directory if it exists.
    $ ansible -i hosts -m win_iis_virtualdirectory -a "name='somedirectory' site=somesite state=absent" host
    
    # This creates a virtual directory on an application if it doesn't exist.
    $ ansible -i hosts -m win_iis_virtualdirectory -a "name='somedirectory' site=somesite application=someapp state=present physical_path=c:\virtualdirectory\some" host




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

