# freebsd_mailserver_spamassassin

[![quality](https://img.shields.io/ansible/quality/27910)](https://galaxy.ansible.com/vbotka/freebsd_mailserver_spamassassin)
[![Build Status](https://travis-ci.org/vbotka/ansible-freebsd-mailserver-spamassassin.svg?branch=master)](https://travis-ci.org/vbotka/ansible-freebsd-mailserver-spamassassin)
[![GitHub tag](https://img.shields.io/github/v/tag/vbotka/ansible-freebsd-mailserver-spamassassin)](https://github.com/vbotka/ansible-freebsd-mailserver-spamassassin/tags)

[Ansible role.](https://galaxy.ansible.com/vbotka/freebsd_mailserver_spamassassin/) FreeBSD. Install and configure Apache SpamAssassin with Postfix.

Feel free to [share your feedback and report issues](https://github.com/vbotka/ansible-freebsd-sieve/issues).

[Contributions are welcome](https://github.com/firstcontributions/first-contributions).


## Requirements and dependencies

### Roles

The dependencies are not listed in the meta file. Install them manually.

- [vbotka.freebsd_mailserver](https://galaxy.ansible.com/vbotka/freebsd_mailserver/) Install and configure Postfix and Dovecot.
- [vbotka.ansible_lib](https://galaxy.ansible.com/vbotka/ansible_lib) Library of Ansible tasks.

### Collections

* community.general


## Variables

See the defaults and examples in vars.


## Workflow

1) Change shell to /bin/sh if necessary

```bash
shell> ansible mailserver -e 'ansible_shell_type=csh ansible_shell_executable=/bin/csh' -a 'sudo pw usermod freebsd -s /bin/sh'
```

2) Install roles

```bash
shell> ansible-galaxy role install vbotka.freebsd_mailserver
shell> ansible-galaxy role install vbotka.freebsd_mailserver_spamassassin
shell> ansible-galaxy role install vbotka.ansible_lib
```

3) Install the collection if necessary

```bash
shell> ansible-galaxy collection install community.general
```

4) Fit variables to your needs.

By default, the daemon *sa-spamd* is disabled (*fm_sa_spamd_enable: false*).

5) Create playbook

```yaml
shell> cat freebsd-mailserver.yml

- hosts: mailserver
  roles:
    - vbotka.freebsd_mailserver
    - vbotka.freebsd_mailserver_spamassassin
```

6) Install and configure Postfix with SpamAssassin

```bash
shell> ansible-playbook freebsd-mailserver.yml
```

6) Consider to test the mailserver with http://mxtoolbox.com/


## Ansible lint

Use the configuration file *.ansible-lint.local* when running
*ansible-lint*. Some rules might be disabled and some warnings might
be ignored. See the notes in the configuration file.

```bash
shell> ansible-lint -c .ansible-lint.local
```


## References

- [Integrating SpamAssassin into Postfix using spamd](https://wiki.apache.org/spamassassin/IntegratedSpamdInPostfix)


## License

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


## Author Information

[Vladimir Botka](https://botka.info)
