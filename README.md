# ansible-role-stackdriver

## Overview
Adds google yum repos for stackdriver, fluentd, google-fluentd-catch-all-config and then installs them

#### Variables
```
---
stackdriver_logging_repo: https://packages.cloud.google.com/yum/repos/google-cloud-logging-el{{ ansible_distribution_major_version }}
stackdriver_logging_repo_suffix: '$basearch'
stackdriver_monitoring_repo: https://packages.cloud.google.com/yum/repos/google-cloud-monitoring-el{{ ansible_distribution_major_version }}
stackdriver_monitoring_repo_suffix: '$basearch'
gpgkeys: https://packages.cloud.google.com/yum/doc/yum-key.gpg,https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
stackdriver_sysconfig: /etc/sysconfig/stackdriver
packages:
  - stackdriver-agent
  - google-fluentd
  - google-fluentd-catch-all-config
stackdriver_collectd_service: stackdriver-agent
stackdriver_restart: false (whether to restart the agent every hour)
stackdriver_tail_logs: [] (list of extra log configs to tail)
```


#### Sample playbook
```
---
- hosts: localhost
  roles:
  - role: ansible-role-stackdriver
  ```
