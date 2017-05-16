.. _sorcery:


sorcery - Package manager for Source Mage GNU/Linux
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages "spells" on Source Mage GNU/Linux using *sorcery* toolchain


Requirements (on host that executes module)
-------------------------------------------

  * bash


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
                <tr><td>cache_valid_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Time in seconds to invalidate grimoire collection on update</div><div>especially useful for SCM and rsync grimoires</div><div>makes sense only in pair with <code>update_cache</code></div>        </td></tr>
                <tr><td>depends<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Comma-separated list of _optional_ dependencies to build a spell (or make sure it is built) with; use +/- in front of dependency to turn it on/off ('+' is optional though)</div><div>this option is ignored if <code>name</code> parameter is equal to '*' or contains more than one spell</div><div>providers must be supplied in the form recognized by Sorcery, e.g. 'openssl(SSL)'</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the spell</div><div>multiple names can be given, separated by commas</div><div>special value '*' in conjunction with states <code>latest</code> or <code>rebuild</code> will update or rebuild the whole system respectively</div></br>
    <div style="font-size: small;">aliases: spell<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>latest</li><li>absent</li><li>cast</li><li>dispelled</li><li>rebuild</li></ul></td>
        <td><div>Whether to cast, dispel or rebuild a package</div><div>state <code>cast</code> is an equivalent of <code>present</code>, not <code>latest</code></div><div>state <code>latest</code> always triggers <code>update_cache=yes</code></div><div>state <code>rebuild</code> implies cast of all specified spells, not only those existed before</div>        </td></tr>
                <tr><td>update<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to update sorcery scripts at the very first stage</div>        </td></tr>
                <tr><td>update_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to update grimoire collection before casting spells</div></br>
    <div style="font-size: small;">aliases: update_codex<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Make sure spell 'foo' is installed
    - sorcery:
        spell: foo
        state: present
    
    # Make sure spells 'foo', 'bar' and 'baz' are removed
    - sorcery:
        spell: foo,bar,baz
        state: absent
    
    # Make sure spell 'foo' with dependencies 'bar' and 'baz' is installed
    - sorcery:
        spell: foo
        depends: bar,baz
        state: present
    
    # Make sure spell 'foo' with 'bar' and without 'baz' dependencies is installed
    - sorcery:
        spell: foo
        depends: +bar,-baz
        state: present
    
    # Make sure spell 'foo' with libressl (providing SSL) dependency is installed
    - sorcery:
        spell: foo
        depends: libressl(SSL)
        state: present
    
    # Playbook: make sure spells with/without required dependencies (if any) are installed
    - sorcery:
        name: "{{ item.spell }}"
        depends: "{{ item.depends | default(None) }}"
        state: present
      with_items:
        - { spell: 'vifm', depends: '+file,-gtk+2' }
        - { spell: 'fwknop', depends: 'gpgme' }
        - { spell: 'pv,tnftp,tor' }
    
    # Install the latest version of spell 'foo' using regular glossary
    - sorcery:
        name: foo
        state: latest
    
    # Rebuild spell 'foo'
    - sorcery:
        spell: foo
        state: rebuild
    
    # Rebuild the whole system, but update Sorcery and Codex first
    - sorcery:
        spell: '*'
        state: rebuild
        update: yes
        update_cache: yes
    
    # Refresh the grimoire collection if it's 1 day old using native sorcerous alias
    - sorcery:
        update_codex: yes
        cache_valid_time: 86400
    
    # Update only Sorcery itself
    - sorcery:
        update: yes


Notes
-----

.. note::
    - When all three components are selected, the update goes by the sequence -- Sorcery -> Grimoire(s) -> Spell(s); you cannot override it.
    - grimoire handling (i.e. add/remove, including SCM/rsync versions) is not yet supported.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
