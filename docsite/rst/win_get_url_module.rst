.. _win_get_url:


win_get_url - Fetches a file from a given URL
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 1


Synopsis
--------

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
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The absolute path of the location to save the file at the URL. Be sure to include a filename and extension as appropriate.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, will always download the file.  If <code>no</code>, will only download the file if it does not exist or the remote file has been modified more recently than the local file.  This works by sending an http HEAD request to retrieve last modified time of the requested resource, so for this to work, the remote web server must support HEAD requests.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Basic authentication password</div></td></tr>
            <tr>
    <td>proxy_password<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Proxy authentication password</div></td></tr>
            <tr>
    <td>proxy_url<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The full URL of the proxy server to download through.</div></td></tr>
            <tr>
    <td>proxy_username<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Proxy authentication username</div></td></tr>
            <tr>
    <td>skip_certificate_validation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Skip SSL certificate validation if true</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The full URL of a file to download</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Basic authentication username</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Downloading a JPEG and saving it to a file with the ansible command.
    # Note the "dest" is quoted rather instead of escaping the backslashes
    $ ansible -i hosts -c winrm -m win_get_url -a "url=http://www.example.com/earthrise.jpg dest='C:\\Users\\Administrator\\earthrise.jpg'" all
    
    # Playbook example
    - name: Download earthrise.jpg to 'C:\\Users\\RandomUser\\earthrise.jpg'
      win_get_url:
        url: 'http://www.example.com/earthrise.jpg'
        dest: 'C:\\Users\\RandomUser\\earthrise.jpg'
    
    - name: Download earthrise.jpg to 'C:\\Users\\RandomUser\\earthrise.jpg' only if modified
      win_get_url:
        url: 'http://www.example.com/earthrise.jpg'
        dest: 'C:\\Users\\RandomUser\\earthrise.jpg'
        force: no
    
    - name: Download earthrise.jpg to 'C:\\Users\\RandomUser\\earthrise.jpg' through a proxy server.
      win_get_url:
        url: 'http://www.example.com/earthrise.jpg'
        dest: 'C:\\Users\\RandomUser\\earthrise.jpg'
        proxy_url: 'http://10.0.0.1:8080'
        proxy_username: 'username'
        proxy_password: 'password'

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
        <td> url </td>
        <td> requested url </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> http://www.example.com/earthrise.jpg </td>
    </tr>
            <tr>
        <td> dest </td>
        <td> destination file/path </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> C:\Users\RandomUser\earthrise.jpg </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

