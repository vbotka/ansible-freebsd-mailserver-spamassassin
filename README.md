freebsd-mailserver-spamassassin
===============================

This role installs and configures spamassassin on FreeBSD.


Requirements
------------

vbotka.ansible-freebsd-mailserver


Variables
---------

TBD (Check the defaults).


Workflow
--------

1) Change shell to /bin/sh.

```
ansible mailserver -e 'ansible_shell_type=csh ansible_shell_executable=/bin/csh' -a 'sudo pw usermod freebsd -s /bin/sh'
```

2) Install role.

```
ansible-galaxy install vbotka.ansible-freebsd-mailserver-spamassassin
```

3) Fit variables.

```
~/.ansible/roles/ansible-freebsd-mailserver-spamassassin/vars/main.yml
```

4) Create playbook.

```
> cat ~/.ansible/playbooks/freebsd-mailserver.yml
---
- hosts: mailserver
  become: yes
  become_method: sudo
  roles:
# mailserver-spamassassin run mailserver role as a dependency
#   - role: vbotka.ansible-freebsd-mailserver
    - role: vbotka.ansible-freebsd-mailserver-spamassassin
```

5) Install and configure the mailserver with spamassassin.

```
ansible-playbook ~/.ansible/playbooks/freebsd-mailserver.yml
```

6) Consider to test the mailserver with http://mxtoolbox.com/


License
-------

BSD


Author Information
------------------

[Vladimir Botka](https://botka.link)


References
----------

[Integrating SpamAssassin into Postfix using spamd](https://wiki.apache.org/spamassassin/IntegratedSpamdInPostfix)

