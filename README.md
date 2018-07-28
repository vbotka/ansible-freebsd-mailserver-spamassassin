freebsd_mailserver_spamassassin
===============================

[![Build Status](https://travis-ci.org/vbotka/ansible-freebsd-mailserver-spamassassin.svg?branch=master)](https://travis-ci.org/vbotka/ansible-freebsd-mailserver-spamassassin)

[Ansible role.](https://galaxy.ansible.com/vbotka/freebsd_mailserver_spamassassin/) FreeBSD. Install and configure Apache SpamAssassin with Postfix.


Requirements
------------

- [vbotka.freebsd_mailserver](https://galaxy.ansible.com/vbotka/freebsd_mailserver/)


Variables
---------

TBD. Review the defaults and examples in vars.


Workflow
--------

1) Change shell to /bin/sh.

```
# ansible mailserver -e 'ansible_shell_type=csh ansible_shell_executable=/bin/csh' -a 'sudo pw usermod freebsd -s /bin/sh'
```

2) Install role.

```
# ansible-galaxy install vbotka.freebsd_mailserver_spamassassin
```

3) Fit variables.

```
# editor vbotka.freebsd_mailserver_spamassassin/vars/main.yml
```

By default the daemon *sa-spamd* is disabled *fm_sa_spamd_enable: False*.

4) Create playbook.

```
# cat freebsd-mailserver.yml

- hosts: mailserver
  roles:
# freebsd_mailserver_spamassassin runs freebsd_mailserver role as a dependency
#   - vbotka.freebsd_mailserver
    - vbotka.freebsd_mailserver_spamassassin
```

5) Install and configure Postfix with SpamAssassin.

```
# ansible-playbook freebsd-mailserver.yml
```

6) Consider to test the mailserver with http://mxtoolbox.com/


License
-------

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


Author Information
------------------

[Vladimir Botka](https://botka.link)


References
----------

- [Integrating SpamAssassin into Postfix using spamd](https://wiki.apache.org/spamassassin/IntegratedSpamdInPostfix)
