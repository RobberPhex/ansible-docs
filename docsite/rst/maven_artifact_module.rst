.. _maven_artifact:


maven_artifact - Downloads an Artifact from a Maven Repository
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Downloads an artifact from a maven repository given the maven coordinates provided to the module. Can retrieve
snapshots or release versions of the artifact and will resolve the latest available version if one is not
available.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * lxml
  * boto if using a S3 repository (s3://...)


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
    <td>artifact_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The maven artifactId coordinate</div></td></tr>
            <tr>
    <td>classifier<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The maven classifier coordinate</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path where the artifact should be written to</div></td></tr>
            <tr>
    <td>extension<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>jar</td>
        <td><ul></ul></td>
        <td><div>The maven type/extension coordinate</div></td></tr>
            <tr>
    <td>group_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The Maven groupId coordinate</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password to authenticate with to the Maven Repository. Use AWS secret access key of the repository is hosted on S3</div></br>
        <div style="font-size: small;">aliases: aws_secret_access_key<div></td></tr>
            <tr>
    <td>repository_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://repo1.maven.org/maven2</td>
        <td><ul></ul></td>
        <td><div>The URL of the Maven Repository to download from.</div><div>Use s3://... if the repository is hosted on Amazon S3, added in version 2.2.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The desired state of the artifact</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username to authenticate as to the Maven Repository. Use AWS secret key of the repository is hosted on S3</div></br>
        <div style="font-size: small;">aliases: aws_secret_key<div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.9.3)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be set to <code>no</code> when no other option exists.</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>latest</td>
        <td><ul></ul></td>
        <td><div>The maven version coordinate</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Download the latest version of the JUnit framework artifact from Maven Central
    - maven_artifact: group_id=junit artifact_id=junit dest=/tmp/junit-latest.jar
    
    # Download JUnit 4.11 from Maven Central
    - maven_artifact: group_id=junit artifact_id=junit version=4.11 dest=/tmp/junit-4.11.jar
    
    # Download an artifact from a private repository requiring authentication
    - maven_artifact: group_id=com.company artifact_id=library-name repository_url=https://repo.company.com/maven username=user password=pass dest=/tmp/library-name-latest.jar
    
    # Download a WAR File to the Tomcat webapps directory to be deployed
    - maven_artifact: group_id=com.company artifact_id=web-app extension=war repository_url=https://repo.company.com/maven dest=/var/lib/tomcat7/webapps/web-app.war




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

