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
HTTP redirects can redirect from HTTP to HTTPS so you should be sure that your proxy environment for both protocols is correct.




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
    <td>checksum<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If a checksum is passed to this parameter, the digest of the destination file will be calculated after it is downloaded to ensure its integrity and verify that the transfer completed successfully. Format: &lt;algorithm&gt;:&lt;checksum&gt;, e.g.: checksum="sha256:D98291AC[...]B6DC7B97" If you worry about portability, only the sha1 algorithm is available on all platforms and python versions.  The third party hashlib library can be installed for access to additional algorithms. Additionaly, if a checksum is passed to this parameter, and the file exist under the <code>dest</code> location, the destination_checksum would be calculated, and if checksum equals destination_checksum, the file download would be skipped (unless <code>force</code> is true). </div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>absolute path of where to download the file to.</div><div>If <code>dest</code> is a directory, either the server provided filename or, if none provided, the base name of the URL on the remote server will be used. If a directory, <code>force</code> has no effect. If <code>dest</code> is a directory, the file will always be downloaded (regardless of the force option), but replaced only if the contents changed.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code> and <code>dest</code> is not a directory, will download the file every time and replace the file if the contents change. If <code>no</code>, the file will only be downloaded if the destination does not exist. Generally should be <code>yes</code> only for small local files. Prior to 0.6, this module behaved as if <code>yes</code> was the default.</div></br>
        <div style="font-size: small;">aliases: thirsty<div></td></tr>
            <tr>
    <td>force_basic_auth<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>httplib2, the library used by the uri module only sends authentication information when a webservice responds to an initial request with a 401 status. Since some basic auth services do not properly send a 401, logins will fail. This option forces the sending of the Basic authentication header upon initial request.</div></td></tr>
            <tr>
    <td>headers<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Add custom HTTP headers to a request in the format "key:value,key:value"</div></td></tr>
            <tr>
    <td>others<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>all arguments accepted by the <span class='module'>file</span> module also work here</div></td></tr>
            <tr>
    <td>sha256sum<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If a SHA-256 checksum is passed to this parameter, the digest of the destination file will be calculated after it is downloaded to ensure its integrity and verify that the transfer completed successfully. This option is deprecated. Use 'checksum'.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Timeout for URL request</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>HTTP, HTTPS, or FTP URL in the form (http|https|ftp)://[user[:pass]]@host.domain[:port]/path</div></td></tr>
            <tr>
    <td>url_password<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password for use in HTTP basic authentication. If the <code>url_username</code> parameter is not specified, the <code>url_password</code> parameter will not be used.</div></td></tr>
            <tr>
    <td>url_username<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username for use in HTTP basic authentication. This parameter can be used without <code>url_password</code> for sites that allow empty passwords.</div></td></tr>
            <tr>
    <td>use_proxy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if <code>no</code>, it will not use a proxy, even if one is defined in an environment variable on the target hosts.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: download foo.conf
      get_url: url=http://example.com/path/file.conf dest=/etc/foo.conf mode=0440
    
    - name: download file and force basic auth
      get_url: url=http://example.com/path/file.conf dest=/etc/foo.conf force_basic_auth=yes
    
    - name: download file with custom HTTP headers
      get_url: url=http://example.com/path/file.conf dest=/etc/foo.conf headers='key:value,key:value'
    
    - name: download file with check
      get_url: url=http://example.com/path/file.conf dest=/etc/foo.conf checksum=sha256:b5bb9d8014a0f9b1d61e21e796d78dccdf1352f23cd32812f4850b878ae4944c
      get_url: url=http://example.com/path/file.conf dest=/etc/foo.conf checksum=md5:66dffb5228a211e61d6d7ef4a86f5758
    
    - name: download file from a file path
      get_url: url="file:///tmp/afile.txt" dest=/tmp/afilecopy.txt  




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

