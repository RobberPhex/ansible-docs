.. _s3_sync:


s3_sync - Efficiently upload multiple files to S3
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The S3 module is great, but it is very slow for a large volume of files- even a dozen will be noticeable. In addition to speed, it handles globbing, inclusions/exclusions, mime types, expiration mapping, recursion, and smart directory mapping.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * boto


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
                <tr><td>aws_access_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS access key. If not set then the value of the AWS_ACCESS_KEY_ID, AWS_ACCESS_KEY or EC2_ACCESS_KEY environment variable is used.</div></br>
    <div style="font-size: small;">aliases: ec2_access_key, access_key<div>        </td></tr>
                <tr><td>aws_secret_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS secret key. If not set then the value of the AWS_SECRET_ACCESS_KEY, AWS_SECRET_KEY, or EC2_SECRET_KEY environment variable is used.</div></br>
    <div style="font-size: small;">aliases: ec2_secret_key, secret_key<div>        </td></tr>
                <tr><td>bucket<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Bucket name.</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>exclude<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>.*</td>
        <td></td>
        <td><div>Shell pattern-style file matching.</div><div>Used after include to remove files (for instance, skip "*.txt")</div><div>For multiple patterns, comma-separate them.</div>        </td></tr>
                <tr><td>file_change_strategy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>date_size</td>
        <td><ul><li>force</li><li>checksum</li><li>date_size</li></ul></td>
        <td><div>Difference determination method to allow changes-only syncing. Unlike rsync, files are not patched- they are fully skipped or fully uploaded.</div><div>date_size will upload if file sizes don't match or if local file modified date is newer than s3's version</div><div>checksum will compare etag values based on s3's implementation of chunked md5s.</div><div>force will always upload all files.</div>        </td></tr>
                <tr><td>file_root<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>File/directory path for synchronization. This is a local path.</div><div>This root path is scrubbed from the key name, so subdirectories will remain as keys.</div>        </td></tr>
                <tr><td>include<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td></td>
        <td><div>Shell pattern-style file matching.</div><div>Used before exclude to determine eligible files (for instance, only "*.gif")</div><div>For multiple patterns, comma-separate them.</div>        </td></tr>
                <tr><td>key_prefix<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>In addition to file path, prepend s3 path with this prefix. Module will add slash at end of prefix if necessary.</div>        </td></tr>
                <tr><td>mime_map<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dict entry from extension to MIME type. This will override any default/sniffed MIME type. For example <code>{".txt": "application/text", ".yml": "appication/text"}</code></div>        </td></tr>
                <tr><td>mode<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>push</td>
        <td><ul><li>push</li></ul></td>
        <td><div>sync direction.</div>        </td></tr>
                <tr><td>permission<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li></li><li>private</li><li>public-read</li><li>public-read-write</li><li>authenticated-read</li><li>aws-exec-read</li><li>bucket-owner-read</li><li>bucket-owner-full-control</li></ul></td>
        <td><div>Canned ACL to apply to synced files.</div><div>Changing this ACL only changes newly synced files, it does not trigger a full reupload.</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
    <div style="font-size: small;">aliases: aws_region, ec2_region<div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: basic upload
      s3_sync:
        bucket: tedder
        file_root: roles/s3/files/
    
    - name: all the options
      s3_sync:
        bucket: tedder
        file_root: roles/s3/files
        mime_map:
          .yml: application/text
          .json: application/text
        key_prefix: config_files/web
        file_change_strategy: force
        permission: public-read
        include: "*"
        exclude: "*.txt,.*"

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
        <td> uploaded </td>
        <td> file listing (dicts) of files that were actually uploaded </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> [{'s3_path': 's3sync/policy.json', 'whysize': '151 / 151', 'fullpath': 'roles/cf/files/policy.json', 'chopped_path': 'policy.json', 'bytes': 151, 'whytime': '1477931637 / 1477931489'}] </td>
    </tr>
            <tr>
        <td> filelist_s3 </td>
        <td> file listing (dicts) including information about previously-uploaded versions </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> [{'s3_path': 's3sync/policy.json', 'modified_epoch': 1477416706, 'fullpath': 'roles/cf/files/policy.json', 'chopped_path': 'policy.json', 'bytes': 151, 'mime_type': 'application/json'}] </td>
    </tr>
            <tr>
        <td> filelist_local_etag </td>
        <td> file listing (dicts) including calculated local etag </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> [{'s3_path': 's3sync/policy.json', 'modified_epoch': 1477416706, 'fullpath': 'roles/cf/files/policy.json', 'chopped_path': 'policy.json', 'bytes': 151, 'mime_type': 'application/json'}] </td>
    </tr>
            <tr>
        <td> filelist_initial </td>
        <td> file listing (dicts) from inital globbing </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> [{'modified_epoch': 1477416706, 'fullpath': 'roles/cf/files/policy.json', 'chopped_path': 'policy.json', 'bytes': 151}] </td>
    </tr>
            <tr>
        <td> filelist_actionable </td>
        <td> file listing (dicts) of files that will be uploaded after the strategy decision </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> [{'s3_path': 's3sync/policy.json', 'whysize': '151 / 151', 'modified_epoch': 1477931256, 'bytes': 151, 'whytime': '1477931256 / 1477929260', 'fullpath': 'roles/cf/files/policy.json', 'chopped_path': 'policy.json', 'mime_type': 'application/json'}] </td>
    </tr>
            <tr>
        <td> filelist_typed </td>
        <td> file listing (dicts) with calculated or overridden mime types </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> [{'modified_epoch': 1477416706, 'fullpath': 'roles/cf/files/policy.json', 'chopped_path': 'policy.json', 'bytes': 151, 'mime_type': 'application/json'}] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
    - Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
    - ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
