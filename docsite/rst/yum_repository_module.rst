.. _yum_repository:


yum_repository - Add and remove YUM repositories
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove YUM repositories in RPM-based Linux distributions.




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
    <td>async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If set to <code>yes</code> Yum will download packages and metadata from this repo in parallel, if possible.</div></td></tr>
            <tr>
    <td>bandwidth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Maximum available network bandwidth in bytes/second. Used with the <em>throttle</em> option.</div><div>If <em>throttle</em> is a percentage and bandwidth is <code>0</code> then bandwidth throttling will be disabled. If <em>throttle</em> is expressed as a data rate (bytes/sec) then this option is ignored. Default is <code>0</code> (no bandwidth throttling).</div></td></tr>
            <tr>
    <td>baseurl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL to the directory where the yum repository's 'repodata' directory lives.</div><div>This or the <em>mirrorlist</em> parameter is required if <em>state</em> is set to <code>present</code>.</div></td></tr>
            <tr>
    <td>cost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1000</td>
        <td><ul></ul></td>
        <td><div>Relative cost of accessing this repository. Useful for weighing one repo's packages as greater/less than any other.</div></td></tr>
            <tr>
    <td>deltarpm_metadata_percentage<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>100</td>
        <td><ul></ul></td>
        <td><div>When the relative size of deltarpm metadata vs pkgs is larger than this, deltarpm metadata is not downloaded from the repo. Note that you can give values over <code>100</code>, so <code>200</code> means that the metadata is required to be half the size of the packages. Use <code>0</code> to turn off this check, and always download metadata.</div></td></tr>
            <tr>
    <td>deltarpm_percentage<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>75</td>
        <td><ul></ul></td>
        <td><div>When the relative size of delta vs pkg is larger than this, delta is not used. Use <code>0</code> to turn off delta rpm processing. Local repositories (with file:// <em>baseurl</em>) have delta rpms turned off by default.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A human readable string describing the repository.</div><div>This parameter is only required if <em>state</em> is set to <code>present</code>.</div></td></tr>
            <tr>
    <td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This tells yum whether or not use this repository.</div></td></tr>
            <tr>
    <td>enablegroups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Determines whether yum will allow the use of package groups for this repository.</div></td></tr>
            <tr>
    <td>exclude<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of packages to exclude from updates or installs. This should be a space separated list. Shell globs using wildcards (eg. <code>*</code> and <code>?</code>) are allowed.</div><div>The list can also be a regular YAML array.</div></td></tr>
            <tr>
    <td>failovermethod<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>roundrobin</td>
        <td><ul><li>roundrobin</li><li>priority</li></ul></td>
        <td><div><code>roundrobin</code> randomly selects a URL out of the list of URLs to start with and proceeds through each of them as it encounters a failure contacting the host.</div><div><code>priority</code> starts from the first <em>baseurl</em> listed and reads through them sequentially.</div></td></tr>
            <tr>
    <td>file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File to use to save the repo in. Defaults to the value of <em>name</em>.</div></td></tr>
            <tr>
    <td>gpgcakey<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A URL pointing to the ASCII-armored CA key file for the repository.</div></td></tr>
            <tr>
    <td>gpgcheck<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Tells yum whether or not it should perform a GPG signature check on packages.</div></td></tr>
            <tr>
    <td>gpgkey<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A URL pointing to the ASCII-armored GPG key file for the repository.</div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the group that should own the file/directory, as would be fed to <em>chown</em></div></td></tr>
            <tr>
    <td>http_caching<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>all</td>
        <td><ul><li>all</li><li>packages</li><li>none</li></ul></td>
        <td><div>Determines how upstream HTTP caches are instructed to handle any HTTP downloads that Yum does.</div><div><code>all</code> means that all HTTP downloads should be cached.</div><div><code>packages</code> means that only RPM package downloads should be cached (but not repository metadata downloads).</div><div><code>none</code> means that no HTTP downloads should be cached.</div></td></tr>
            <tr>
    <td>include<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Include external configuration file. Both, local path and URL is supported. Configuration file will be inserted at the position of the <em>include=</em> line. Included files may contain further include lines. Yum will abort with an error if an inclusion loop is detected.</div></td></tr>
            <tr>
    <td>includepkgs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of packages you want to only use from a repository. This should be a space separated list. Shell globs using wildcards (eg. <code>*</code> and <code>?</code>) are allowed. Substitution variables (e.g. <code>$releasever</code>) are honored here.</div><div>The list can also be a regular YAML array.</div></td></tr>
            <tr>
    <td>ip_resolve<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>whatever</td>
        <td><ul><li>4</li><li>6</li><li>IPv4</li><li>IPv6</li><li>whatever</li></ul></td>
        <td><div>Determines how yum resolves host names.</div><div><code>4</code> or <code>IPv4</code> - resolve to IPv4 addresses only.</div><div><code>6</code> or <code>IPv6</code> - resolve to IPv6 addresses only.</div></td></tr>
            <tr>
    <td>keepalive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This tells yum whether or not HTTP/1.1 keepalive should be used with this repository. This can improve transfer speeds by using one connection when downloading multiple files from a repository.</div></td></tr>
            <tr>
    <td>keepcache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>0</li><li>1</li></ul></td>
        <td><div>Either <code>1</code> or <code>0</code>. Determines whether or not yum keeps the cache of headers and packages after successful installation.</div></td></tr>
            <tr>
    <td>metadata_expire<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>21600</td>
        <td><ul></ul></td>
        <td><div>Time (in seconds) after which the metadata will expire.</div><div>Default value is 6 hours.</div></td></tr>
            <tr>
    <td>metadata_expire_filter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>read-only:present</td>
        <td><ul><li>never</li><li>read-only:past</li><li>read-only:present</li><li>read-only:future</li></ul></td>
        <td><div>Filter the <em>metadata_expire</em> time, allowing a trade of speed for accuracy if a command doesn't require it. Each yum command can specify that it requires a certain level of timeliness quality from the remote repos. from "I'm about to install/upgrade, so this better be current" to "Anything that's available is good enough".</div><div><code>never</code> - Nothing is filtered, always obey <em>metadata_expire</em>.</div><div><code>read-only:past</code> - Commands that only care about past information are filtered from metadata expiring. Eg. <em>yum history</em> info (if history needs to lookup anything about a previous transaction, then by definition the remote package was available in the past).</div><div><code>read-only:present</code> - Commands that are balanced between past and future. Eg. <em>yum list yum</em>.</div><div><code>read-only:future</code> - Commands that are likely to result in running other commands which will require the latest metadata. Eg. <em>yum check-update</em>.</div><div>Note that this option does not override "yum clean expire-cache".</div></td></tr>
            <tr>
    <td>metalink<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies a URL to a metalink file for the repomd.xml, a list of mirrors for the entire repository are generated by converting the mirrors for the repomd.xml file to a <em>baseurl</em>.</div></td></tr>
            <tr>
    <td>mirrorlist<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies a URL to a file containing a list of baseurls.</div><div>This or the <em>baseurl</em> parameter is required if <em>state</em> is set to <code>present</code>.</div></td></tr>
            <tr>
    <td>mirrorlist_expire<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>21600</td>
        <td><ul></ul></td>
        <td><div>Time (in seconds) after which the mirrorlist locally cached will expire.</div><div>Default value is 6 hours.</div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>mode the file or directory should be. For those used to <em>/usr/bin/chmod</em> remember that modes are actually octal numbers (like 0644). Leaving off the leading zero will likely have unexpected results. As of version 1.8, the mode may be specified as a symbolic mode (for example, <code>u+rwx</code> or <code>u=rw,g=r,o=r</code>).</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Unique repository ID.</div><div>This parameter is only required if <em>state</em> is set to <code>present</code> or <code>absent</code>.</div></td></tr>
            <tr>
    <td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the user that should own the file/directory, as would be fed to <em>chown</em></div></td></tr>
            <tr>
    <td>params<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Option used to allow the user to overwrite any of the other options. To remove an option, set the value of the option to <code>null</code>.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password to use with the username for basic authentication.</div></td></tr>
            <tr>
    <td>priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>99</td>
        <td><ul></ul></td>
        <td><div>Enforce ordered protection of repositories. The value is an integer from 1 to 99.</div><div>This option only works if the YUM Priorities plugin is installed.</div></td></tr>
            <tr>
    <td>protect<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Protect packages from updates from other repositories.</div></td></tr>
            <tr>
    <td>proxy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL to the proxy server that yum should use. Set to <code>_none_</code> to disable the global proxy setting.</div></td></tr>
            <tr>
    <td>proxy_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Username to use for proxy.</div></td></tr>
            <tr>
    <td>proxy_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password for this proxy.</div></td></tr>
            <tr>
    <td>repo_gpgcheck<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>This tells yum whether or not it should perform a GPG signature check on the repodata from this repository.</div></td></tr>
            <tr>
    <td>reposdir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/yum.repos.d</td>
        <td><ul></ul></td>
        <td><div>Directory where the <code>.repo</code> files will be stored.</div></td></tr>
            <tr>
    <td>retries<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Set the number of times any attempt to retrieve a file should retry before returning an error. Setting this to <code>0</code> makes yum try forever.</div></td></tr>
            <tr>
    <td>s3_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enables support for S3 repositories.</div><div>This option only works if the YUM S3 plugin is installed.</div></td></tr>
            <tr>
    <td>selevel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>s0</td>
        <td><ul></ul></td>
        <td><div>level part of the SELinux file context. This is the MLS/MCS attribute, sometimes known as the <code>range</code>. <code>_default</code> feature works as for <em>seuser</em>.</div></td></tr>
            <tr>
    <td>serole<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>role part of SELinux file context, <code>_default</code> feature works as for <em>seuser</em>.</div></td></tr>
            <tr>
    <td>setype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>type part of SELinux file context, <code>_default</code> feature works as for <em>seuser</em>.</div></td></tr>
            <tr>
    <td>seuser<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>user part of SELinux file context. Will default to system policy, if applicable. If set to <code>_default</code>, it will use the <code>user</code> portion of the policy if available</div></td></tr>
            <tr>
    <td>skip_if_unavailable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If set to <code>yes</code> yum will continue running if this repository cannot be contacted for any reason. This should be set carefully as all repos are consulted for any given command.</div></td></tr>
            <tr>
    <td>ssl_check_cert_permissions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether yum should check the permissions on the paths for the certificates on the repository (both remote and local).</div><div>If we can't read any of the files then yum will force <em>skip_if_unavailable</em> to be <code>yes</code>. This is most useful for non-root processes which use yum on repos that have client cert files which are readable only by root.</div></td></tr>
            <tr>
    <td>sslcacert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the directory containing the databases of the certificate authorities yum should use to verify SSL certificates.</div></td></tr>
            <tr>
    <td>sslclientcert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the SSL client certificate yum should use to connect to repos/remote sites.</div></td></tr>
            <tr>
    <td>sslclientkey<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the SSL client key yum should use to connect to repos/remote sites.</div></td></tr>
            <tr>
    <td>sslverify<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Defines whether yum should verify SSL certificates/hosts at all.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>State of the repo file.</div></td></tr>
            <tr>
    <td>throttle<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enable bandwidth throttling for downloads.</div><div>This option can be expressed as a absolute data rate in bytes/sec. An SI prefix (k, M or G) may be appended to the bandwidth value.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>Number of seconds to wait for a connection before timing out.</div></td></tr>
            <tr>
    <td>ui_repoid_vars<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>releasever basearch</td>
        <td><ul></ul></td>
        <td><div>When a repository id is displayed, append these yum variables to the string if they are used in the <em>baseurl</em>/etc. Variables are appended in the order listed (and found).</div></td></tr>
            <tr>
    <td>unsafe_writes<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Normally this module uses atomic operations to prevent data corruption or inconsistent reads from the target files, sometimes systems are configured or just broken in ways that prevent this. One example are docker mounted files, they cannot be updated atomically and can only be done in an unsafe manner.</div><div>This boolean option allows ansible to fall back to unsafe methods of updating files for those cases in which you do not have any other choice. Be aware that this is subject to race conditions and can lead to data corruption.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Username to use for basic authentication to a repo or really any url.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Add repository
      yum_repository:
        name: epel
        description: EPEL YUM repo
        baseurl: http://download.fedoraproject.org/pub/epel/$releasever/$basearch/
    
    - name: Add multiple repositories into the same file (1/2)
      yum_repository:
        name: epel
        description: EPEL YUM repo
        file: external_repos
        baseurl: http://download.fedoraproject.org/pub/epel/$releasever/$basearch/
        gpgcheck: no
    - name: Add multiple repositories into the same file (2/2)
      yum_repository:
        name: rpmforge
        description: RPMforge YUM repo
        file: external_repos
        baseurl: http://apt.sw.be/redhat/el7/en/$basearch/rpmforge
        mirrorlist: http://mirrorlist.repoforge.org/el7/mirrors-rpmforge
        enabled: no
    
    - name: Remove repository
      yum_repository:
        name: epel
        state: absent
    
    - name: Remove repository from a specific repo file
      yum_repository:
        name: epel
        file: external_repos
        state: absent
    
    #
    # Allow to overwrite the yum_repository parameters by defining the parameters
    # as a variable in the defaults or vars file:
    #
    # my_role_somerepo_params:
    #   # Disable GPG checking
    #   gpgcheck: no
    #   # Remove the gpgkey option
    #   gpgkey: null
    #
    - name: Add Some repo
      yum_repository:
        name: somerepo
        description: Some YUM repo
        baseurl: http://server.com/path/to/the/repo
        gpgkey: http://server.com/keys/somerepo.pub
        gpgcheck: yes
        params: "{{ my_role_somerepo_params }}"

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
        <td> repo </td>
        <td> repository name </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> epel </td>
    </tr>
            <tr>
        <td> state </td>
        <td> state of the target, after execution </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: All comments will be removed if modifying an existing repo file.
.. note:: Section order is preserved in an existing repo file.
.. note:: Parameters in a section are ordered alphabetically in an existing repo file.
.. note:: The repo file will be automatically deleted if it contains no repository.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

