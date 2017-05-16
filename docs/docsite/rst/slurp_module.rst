.. _slurp:


slurp - Slurps a file from remote nodes
+++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module works like :ref:`fetch <fetch>`. It is used for fetching a base64- encoded blob containing the data in a remote file.




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
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The file on the remote system to fetch. This <em>must</em> be a file, not a directory.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Find out what the remote machine's mounts are:
    - slurp:
        src: /proc/mounts
      register: mounts
    
    - debug:
        msg: "{{ mounts['content'] | b64decode }}"
    
    # From the commandline, find the pid of the remote machine's sshd
    # $ ansible host -m slurp -a 'src=/var/run/sshd.pid'
    # host | SUCCESS => {
    #     "changed": false,
    #     "content": "MjE3OQo=",
    #     "encoding": "base64",
    #     "source": "/var/run/sshd.pid"
    # }
    # $ echo MjE3OQo= | base64 -d
    # 2179


Notes
-----

.. note::
    - This module returns an 'in memory' base64 encoded version of the file, take into account that this will require at least twice the RAM as the original file size.
    - See also: :ref:`fetch <fetch>`



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
