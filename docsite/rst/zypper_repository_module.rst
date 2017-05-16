.. _zypper_repository:


zypper_repository - Add and remove Zypper repositories
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove Zypper repositories on SUSE and openSUSE


Requirements (on host that executes module)
-------------------------------------------

  * zypper >= 1.0  # included in openSuSE >= 11.1 or SuSE Linux Enterprise Server/Desktop >= 11.0


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
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>A description of the repository</div></td></tr>
            <tr>
    <td>disable_gpg_check<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to disable GPG signature checking of all packages. Has an effect only if state is <em>present</em>.</div><div>Needs zypper version &gt;= 1.6.2.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>A name for the repository. Not required when adding repofiles.</div></td></tr>
            <tr>
    <td>overwrite_multiple<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Overwrite multiple repository entries, if repositories with both name and URL already exist.</div></td></tr>
            <tr>
    <td>priority<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set priority of repository. Packages will always be installed from the repository with the smallest priority number.</div><div>Needs zypper version &gt;= 1.12.25.</div></td></tr>
            <tr>
    <td>refresh<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enable autorefresh of the repository.</div></td></tr>
            <tr>
    <td>repo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>URI of the repository or .repo file. Required when state=present.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>A source string state.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add NVIDIA repository for graphics drivers
    - zypper_repository: name=nvidia-repo repo='ftp://download.nvidia.com/opensuse/12.2' state=present
    
    # Remove NVIDIA repository
    - zypper_repository: name=nvidia-repo repo='ftp://download.nvidia.com/opensuse/12.2' state=absent
    
    # Add python development repository
    - zypper_repository: repo=http://download.opensuse.org/repositories/devel:/languages:/python/SLE_11_SP3/devel:languages:python.repo




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

