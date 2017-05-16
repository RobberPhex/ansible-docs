.. _cloudfront_facts:


cloudfront_facts - Obtain facts about an AWS CloudFront distribution
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Gets information about an AWS CloudFront distribution


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto3 >= 1.0.0
  * python >= 2.6


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
                <tr><td>all_lists<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get all cloudfront lists that do not require parameters.</div>        </td></tr>
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
                <tr><td>distribution<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get information about a distribution. Requires <em>distribution_id</em> or <em>domain_name_alias</em> to be specified.</div>        </td></tr>
                <tr><td>distribution_config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get the configuration information about a distribution. Requires <em>distribution_id</em> or <em>domain_name_alias</em> to be specified.</div>        </td></tr>
                <tr><td>distribution_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The id of the CloudFront distribution. Used with <em>distribution</em>, <em>distribution_config</em>, <em>invalidation</em>, <em>streaming_distribution</em>, <em>streaming_distribution_config</em>, <em>list_invalidations</em>.</div>        </td></tr>
                <tr><td>domain_name_alias<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Can be used instead of <em>distribution_id</em> - uses the aliased CNAME for the cloudfront distribution to get the distribution id where required.</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>invalidation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get information about an invalidation. Requires <em>invalidation_id</em> to be specified.</div>        </td></tr>
                <tr><td>invalidation_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The id of the invalidation to get information about. Used with <em>invalidation</em>.</div>        </td></tr>
                <tr><td>list_distributions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get a list of cloudfront distributions.</div>        </td></tr>
                <tr><td>list_distributions_by_web_acl_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get a list of distributions using web acl id as a filter. Requires <em>web_acl_id</em> to be set.</div>        </td></tr>
                <tr><td>list_invalidations<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get a list of invalidations. Requires <em>distribution_id</em> or <em>domain_name_alias</em> to be specified.</div>        </td></tr>
                <tr><td>list_origin_access_identities<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get a list of cloudfront origin access identities. Requires <em>origin_access_identity_id</em> to be set.</div>        </td></tr>
                <tr><td>list_streaming_distributions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get a list of streaming distributions.</div>        </td></tr>
                <tr><td>origin_access_identity<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get information about an origin access identity. Requires <em>origin_access_identity_id</em> to be specified.</div>        </td></tr>
                <tr><td>origin_access_identity_config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get the configuration information about an origin access identity. Requires <em>origin_access_identity_id</em> to be specified.</div>        </td></tr>
                <tr><td>origin_access_identity_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The id of the cloudfront origin access identity to get information about.</div>        </td></tr>
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
                <tr><td>streaming_distribution<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get information about a specified RTMP distribution. Requires <em>distribution_id</em> or <em>domain_name_alias</em> to be specified.</div>        </td></tr>
                <tr><td>streaming_distribution_configuration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Get the configuration information about a specified RTMP distribution. Requires <em>distribution_id</em> or <em>domain_name_alias</em> to be specified.</div>        </td></tr>
                <tr><td>summary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Returns a summary of all distributions, streaming distributions and origin_access_identities. This is the default behaviour if no option is selected.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
                <tr><td>web_acl_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Used with <em>list_distributions_by_web_acl_id</em>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    # Get a summary of distributions
    - cloudfront_facts:
        summary: true
    
    # Get information about a distribution
    - cloudfront_facts:
        distribution: true
        distribution_id: my-cloudfront-distribution-id
    
    # Get information about a distribution using the CNAME of the cloudfront distribution.
    - cloudfront_facts:
        distribution: true
        domain_name_alias: www.my-website.com
    
    # Facts are published in ansible_facts['cloudfront'][<distribution_name>]
    - debug:
        msg: "{{ ansible_facts['cloudfront']['my-cloudfront-distribution-id'] }}"
    
    - debug:
        msg: "{{ ansible_facts['cloudfront']['www.my-website.com'] }}"
    
    # Get all information about an invalidation for a distribution.
    - cloudfront_facts:
        invalidation: true
        distribution_id: my-cloudfront-distribution-id
        invalidation_id: my-cloudfront-invalidation-id
    
    # Get all information about a cloudfront origin access identity.
    - cloudfront_facts:
        origin_access_identity: true
        origin_access_identity_id: my-cloudfront-origin-access-identity-id
    
    # Get all information about lists not requiring parameters (ie. list_origin_access_identities, list_distributions, list_streaming_distributions)
    - cloudfront_facts:
        origin_access_identity: true
        origin_access_identity_id: my-cloudfront-origin-access-identity-id
    
    # Get all information about lists not requiring parameters (ie. list_origin_access_identities, list_distributions, list_streaming_distributions)
    - cloudfront_facts:
        all_lists: true

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
        <td> streaming_distribution_configuration </td>
        <td> Describes the streaming configuration information for the distribution. Requires I(distribution_id) or I(domain_name_alias) to be specified.
 </td>
        <td align=center> only if I(streaming_distribution_configuration) is true </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> invalidation </td>
        <td> Describes the invalidation information for the distribution. Requires I(invalidation_id) to be specified and either I(distribution_id) or I(domain_name_alias.)
 </td>
        <td align=center> only if invalidation is true </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> streaming_distribution </td>
        <td> Describes the streaming information for the distribution. Requires I(distribution_id) or I(domain_name_alias) to be specified.
 </td>
        <td align=center> only if I(streaming_distribution) is true </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> origin_access_identity </td>
        <td> Describes the origin access identity information. Requires I(origin_access_identity_id) to be set. </td>
        <td align=center> only if I(origin_access_identity) is true </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> origin_access_identity_configuration </td>
        <td> Describes the origin access identity information configuration information. Requires I(origin_access_identity_id) to be set. </td>
        <td align=center> only if I(origin_access_identity_configuration) is true </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> distribution_config </td>
        <td> Facts about a cloudfront distribution's config. Requires I(distribution_id) or I(domain_name_alias) to be specified.
 </td>
        <td align=center> only if I(distribution_config) is true </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> distribution </td>
        <td> Facts about a cloudfront distribution. Requires I(distribution_id) or I(domain_name_alias) to be specified. Requires I(origin_access_identity_id) to be set.
 </td>
        <td align=center> only if distribution is true </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> summary </td>
        <td> Gives a summary of distributions, streaming distributions and origin access identities. </td>
        <td align=center> as default or if summary is true </td>
        <td align=center> dict </td>
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
