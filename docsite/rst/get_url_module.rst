.. _get_url:


get_url - Downloads files from HTTP, HTTPS, or FTP to node
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Downloads files from HTTP, HTTPS, or FTP to the remote server. The remote server *must* have direct access to the remote resource.
By default, if an environment variable ``<protocol>_proxy`` is set on the target host, requests will be sent through that proxy. This behaviour can be overridden by setting a variable for this task (see `setting the environment <http://docs.ansible.com/playbooks_environment.html>`_), or by using the use_proxy option.

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
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>absolute path of where to download the file to.If <code>dest</code> is a directory, either the server provided filename or, if none provided, the base name of the URL on the remote server will be used. If a directory, <code>force</code> has no effect. If <code>dest</code> is a directory, the file will always be downloaded (regardless of the force option), but replaced only if the contents changed.</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>yes</code> and <code>dest</code> is not a directory, will download the file every time and replace the file if the contents change. If <code>no</code>, the file will only be downloaded if the destination does not exist. Generally should be <code>yes</code> only for small local files. Prior to 0.6, this module behaved as if <code>yes</code> was the default. (added in Ansible 0.7)</td>
    </tr>
            <tr>
    <td>others</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>all arguments accepted by the <span class='module'>file</span> module also work here</td>
    </tr>
            <tr>
    <td>sha256sum</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If a SHA-256 checksum is passed to this parameter, the digest of the destination file will be calculated after it is downloaded to ensure its integrity and verify that the transfer completed successfully. (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td>Timeout for URL request (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>url</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>HTTP, HTTPS, or FTP URL in the form (http|https|ftp)://[user[:pass]]@host.domain[:port]/path</td>
    </tr>
            <tr>
    <td>url_password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The password for use in HTTP basic authentication. If the <code>url_username</code> parameter is not specified, the <code>url_password</code> parameter will not be used. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>url_username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The username for use in HTTP basic authentication. This parameter can be used without <code>url_password</code> for sites that allow empty passwords. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>use_proxy</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>if <code>no</code>, it will not use a proxy, even if one is defined in an environment variable on the target hosts.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</td>
    </tr>
        </table>


.. note:: Requires urllib2


.. note:: Requires urlparse


Examples
--------

.. raw:: html

    <br/>


::

    - name: download foo.conf
      get_url: url=http://example.com/path/file.conf dest=/etc/foo.conf mode=0440
    
    - name: download file with sha256 check
      get_url: url=http://example.com/path/file.conf dest=/etc/foo.conf sha256sum=b5bb9d8014a0f9b1d61e21e796d78dccdf1352f23cd32812f4850b878ae4944c

.. note:: This module doesn't yet support configuration for proxies.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

