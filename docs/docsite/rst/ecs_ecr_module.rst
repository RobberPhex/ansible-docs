.. _ecs_ecr:


ecs_ecr - Manage Elastic Container Registry repositories
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage Elastic Container Registry repositories


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
                <tr><td>delete_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>if yes, remove the policy from the repository</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>force_set_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>if no, prevents setting a policy that would prevent you from setting another policy in the future.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the name of the repository</div>        </td></tr>
                <tr><td>policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>JSON or dict that represents the new policy</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>registry_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS account id associated with the registry.</div><div>If not specified, the default registry is assumed.</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>create or destroy the repository</div>        </td></tr>
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

    # If the repository does not exist, it is created. If it does exist, would not
    # affect any policies already on it.
    - name: ecr-repo
      ecs_ecr: name=super/cool
    
    - name: destroy-ecr-repo
      ecs_ecr: name=old/busted state=absent
    
    - name: Cross account ecr-repo
      ecs_ecr: registry_id=999999999999 name=cross/account
    
    - name: set-policy as object
      ecs_ecr:
        name: needs-policy-object
        policy:
          Version: '2008-10-17'
          Statement:
            - Sid: read-only
              Effect: Allow
              Principal:
                AWS: '{{ read_only_arn }}'
              Action:
                - ecr:GetDownloadUrlForLayer
                - ecr:BatchGetImage
                - ecr:BatchCheckLayerAvailability
    
    - name: set-policy as string
      ecs_ecr:
        name: needs-policy-string
        policy: "{{ lookup('template', 'policy.json.j2') }}"
    
    - name: delete-policy
      ecs_ecr:
        name: needs-no-policy
        delete_policy: yes

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
        <td> state </td>
        <td> The asserted state of the repository (present, absent) </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> name </td>
        <td> The name of the repository </td>
        <td align=center> when state == 'absent' </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> repository </td>
        <td> The created or updated repository </td>
        <td align=center> when state == 'present' </td>
        <td align=center> dict </td>
        <td align=center> {'registryId': '999999999999', 'repositoryName': 'ecr-test-1484664090', 'repositoryArn': 'arn:aws:ecr:us-east-1:999999999999:repository/ecr-test-1484664090', 'createdAt': '2017-01-17T08:41:32-06:00', 'repositoryUri': '999999999999.dkr.ecr.us-east-1.amazonaws.com/ecr-test-1484664090'} </td>
    </tr>
            <tr>
        <td> created </td>
        <td> If true, the repository was created </td>
        <td align=center>  </td>
        <td align=center> boolean </td>
        <td align=center>  </td>
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
