.. _digital_ocean_domain:


digital_ocean_domain - Create/delete a DNS record in DigitalOcean
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Create/delete a DNS record in DigitalOcean.

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
    <td>api_token</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>DigitalOcean api token. (added in Ansible 1.9.5)</td>
    </tr>
            <tr>
    <td>id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Numeric, the droplet id you want to operate on.</td>
    </tr>
            <tr>
    <td>ip</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The IP address to point a domain at.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>String, this is the name of the droplet - must be formatted by hostname rules, or the name of a SSH key, or the name of a domain.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the target.</td>
    </tr>
        </table>


.. note:: Requires python >= 2.6


.. note:: Requires dopy


Examples
--------

.. raw:: html

    <br/>


::

    # Create a domain record
    
    - digital_ocean_domain: >
          state=present
          name=my.digitalocean.domain
          ip=127.0.0.1
    
    # Create a droplet and a corresponding domain record
    
    - digital_ocean: >
          state=present
          name=test_droplet
          size_id=1gb
          region_id=sgp1
          image_id=ubuntu-14-04-x64
      register: test_droplet
    
    - digital_ocean_domain: >
          state=present
          name={{ test_droplet.droplet.name }}.my.domain
          ip={{ test_droplet.droplet.ip_address }}

.. note:: Two environment variables can be used, DO_API_KEY and DO_API_TOKEN. They both refer to the v2 token.
.. note:: As of Ansible 1.9.5 and 2.0, Version 2 of the DigitalOcean API is used, this removes ``client_id`` and ``api_key`` options in favor of ``api_token``.
.. note:: If you are running Ansible 1.9.4 or earlier you might not be able to use the included version of this module as the API version used has been retired.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

