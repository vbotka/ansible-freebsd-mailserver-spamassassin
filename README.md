# freebsd_mailserver_spamassassin

[![Build Status](https://travis-ci.org/vbotka/ansible-freebsd-mailserver-spamassassin.svg?branch=master)](https://travis-ci.org/vbotka/ansible-freebsd-mailserver-spamassassin)

[Ansible role.](https://galaxy.ansible.com/vbotka/freebsd_mailserver_spamassassin/) FreeBSD. Install and configure Apache SpamAssassin with Postfix.

Please feel free to [share your feedback and report issues](https://github.com/vbotka/ansible-freebsd-sieve/issues).

## Dependencies

- [vbotka.freebsd_mailserver](https://galaxy.ansible.com/vbotka/freebsd_mailserver/) Install and configure Postfix and Dovecot.
- [vbotka.ansible_lib](https://galaxy.ansible.com/vbotka/ansible_lib) Library of Ansible tasks.


## Variables

Review the defaults and examples in vars.


## Workflow

1) Change shell to /bin/sh

```
shell> ansible mailserver -e 'ansible_shell_type=csh ansible_shell_executable=/bin/csh' -a 'sudo pw usermod freebsd -s /bin/sh'
```

2) Install role

```
shell> ansible-galaxy install vbotka.freebsd_mailserver_spamassassin
```

3) Fit variables

```
shell> editor vbotka.freebsd_mailserver_spamassassin/vars/main.yml
```

By default the daemon *sa-spamd* is disabled *fm_sa_spamd_enable: False*.

4) Create playbook

```
shell> cat freebsd-mailserver.yml

- hosts: mailserver
  roles:
    - vbotka.freebsd_mailserver
    - vbotka.freebsd_mailserver_spamassassin
```

5) Install and configure Postfix with SpamAssassin

```
shell> ansible-playbook freebsd-mailserver.yml
```

6) Consider to test the mailserver with http://mxtoolbox.com/


## References

- [Integrating SpamAssassin into Postfix using spamd](https://wiki.apache.org/spamassassin/IntegratedSpamdInPostfix)


## License

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


## Author Information

[Vladimir Botka](https://botka.link)
