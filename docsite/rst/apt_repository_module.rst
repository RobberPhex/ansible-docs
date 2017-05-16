.. _apt_repository:


apt_repository - Add and remove APT repositories
++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Add or remove an APT repositories in Ubuntu and Debian.

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
    <td>mode</td>
    <td>no</td>
    <td>420</td>
        <td><ul></ul></td>
        <td>The octal mode for newly created files in sources.list.d (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>repo</td>
    <td>yes</td>
    <td>none</td>
        <td><ul></ul></td>
        <td>A source string for the repository.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td>A source string state.</td>
    </tr>
            <tr>
    <td>update_cache</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Run the equivalent of <code>apt-get update</code> when a change occurs.  Cache updates are run after making changes.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates for the target repo will not be validated. This should only be used on personally controlled sites using self-signed certificates. (added in Ansible 1.8)</td>
    </tr>
        </table>


.. note:: Requires python-apt


Examples
--------

.. raw:: html

    <br/>


::

    # Add specified repository into sources list.
    apt_repository: repo='deb http://archive.canonical.com/ubuntu hardy partner' state=present
    
    # Add source repository into sources list.
    apt_repository: repo='deb-src http://archive.canonical.com/ubuntu hardy partner' state=present
    
    # Remove specified repository from sources list.
    apt_repository: repo='deb http://archive.canonical.com/ubuntu hardy partner' state=absent
    
    # On Ubuntu target: add nginx stable repository from PPA and install its signing key.
    # On Debian target: adding PPA is not available, so it will fail immediately.
    apt_repository: repo='ppa:nginx/stable'

.. note:: This module works on Debian and Ubuntu and requires ``python-apt``.
.. note:: This module supports Debian Squeeze (version 6) as well as its successors.
.. note:: This module treats Debian and Ubuntu distributions separately. So PPA could be installed only on Ubuntu machines.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

