.. _boundary_meter:


boundary_meter - Manage boundary meters
+++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

This module manages boundary meters

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
    <td>apiid</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Organizations boundary API ID</td>
    </tr>
            <tr>
    <td>apikey</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Organizations boundary API KEY</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>meter name</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether to create or remove the client from boundary</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates. (added in Ansible 1.5.1)</td>
    </tr>
        </table>


.. note:: Requires Boundary API access


.. note:: Requires bprobe is required to send data, but not to register a meter


.. note:: Requires Python urllib2


Examples
--------

.. raw:: html

    <br/>


::

    - name: Create meter
      boundary_meter: apiid=AAAAAA api_key=BBBBBB state=present name={{ inventory_hostname }}"
    
    - name: Delete meter
      boundary_meter: apiid=AAAAAA api_key=BBBBBB state=absent name={{ inventory_hostname }}"
    

.. note:: This module does not yet support boundary tags.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

