.. _win_get_url:


win_get_url - Fetches a file from a given URL
+++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.7

Fetches a file from a URL and saves to locally

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
    <td>dest</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>The absolute path of the location to save the file at the URL. Be sure to include a filename and extension as appropriate.</td>
    </tr>
            <tr>
    <td>url</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The full URL of a file to download</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Downloading a JPEG and saving it to a file with the ansible command.
    # Note the "dest" is quoted rather instead of escaping the backslashes
    $ ansible -i hosts -c winrm -m win_get_url -a "url=http://www.example.com/earthrise.jpg dest='C:\Users\Administrator\earthrise.jpg'" all
    
    # Playbook example
    - name: Download earthrise.jpg to 'C:\Users\RandomUser\earthrise.jpg'
      win_get_url:
        url: 'http://www.example.com/earthrise.jpg'
        dest: 'C:\Users\RandomUser\earthrise.jpg'



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

