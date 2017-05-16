.. _win_shortcut:


win_shortcut - Manage shortcuts on Windows
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, manage and delete Windows shortcuts




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
                <tr><td>args<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Additional arguments for the executable defined in <code>src</code>.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description for the shortcut.</div><div>This is usually shown when hoovering the icon.</div>        </td></tr>
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Destination file for the shortcuting file.</div><div>File name should have a <code>.lnk</code> or <code>.url</code> extension.</div>        </td></tr>
                <tr><td>directory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Working directory for executable defined in <code>src</code>.</div>        </td></tr>
                <tr><td>hotkey<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Key combination for the shortcut.</div>        </td></tr>
                <tr><td>icon<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Icon used for the shortcut</div><div>File name should have a <code>.ico</code> extension.</div><div>The file name is followed by a comma and the number in the library file (.dll) or use 0 for an image file.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Executable or URL the shortcut points to.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>When <code>present</code>, creates or updates the shortcut.  When <code>absent</code>, removes the shortcut if it exists.</div>        </td></tr>
                <tr><td>windowstyle<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>default</li><li>maximized</li><li>minimized</li></ul></td>
        <td><div>Influences how the application is displayed when it is launched.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create an application shortcut on the desktop
    - win_shortcut:
        src: C:\Program Files\Mozilla Firefox\Firefox.exe
        dest: C:\Users\Public\Desktop\Mozilla Firefox.lnk
        icon: C:\Program Files\Mozilla Firefox\Firefox.exe,0
    
    # Create the same shortcut using environment variables
    - win_shortcut:
        description: The Mozilla Firefox web browser
        src: '%PROGRAMFILES%\Mozilla Firefox\Firefox.exe'
        dest: '%PUBLIC%\Desktop\Mozilla Firefox.lnk'
        icon: '%PROGRAMFILES\Mozilla Firefox\Firefox.exe,0'
        directory: '%PROGRAMFILES%\Mozilla Firefox'
    
    # Create a URL shortcut to the Ansible website
    - win_shortcut:
        src: 'https://ansible.com/'
        dest: '%PUBLIC%\Desktop\Ansible website.url'
    
    # Create an application shortcut for the Ansible website
    - win_shortcut:
        src: '%PROGRAMFILES%\Google\Chrome\Application\chrome.exe'
        dest: '%PUBLIC%\Desktop\Ansible website.lnk'
        args: '--new-window https://ansible.com/'
        directory: '%PROGRAMFILES%\Google\Chrome\Application'
        icon: '%PROGRAMFILES%\Google\Chrome\Application\chrome.exe,0'


Notes
-----

.. note::
    - The following options can include Windows environment variables: ``dest``, ``args``, ``description``, ``dest``, ``directory``, ``icon`` ``src``
    - Windows has two types of shortcuts: Application and URL shortcuts. URL shortcuts only consists of ``dest`` and ``src``



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
