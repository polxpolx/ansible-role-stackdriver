# ansible-role-stackdriver

## Overview

Adds google yum repos for stackdriver, fluentd, google-fluentd-catch-all-config and then installs them

### Variables

```yaml
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

### Sample playbook

```yaml
---
- hosts: localhost
  roles:
  - role: ansible-role-stackdriver
  ```

### Support for Google Cloud Monitoring agent v6

In order to support the Google Cloud Monitoring agent v6, set the var `stackdriver_monitoring_repo_suffix` to `$basearch-all` (in a host or group var file for instance)

```yaml
# Use Cloud Monitoring Agent 6.X
stackdriver_monitoring_repo_suffix: '$basearch-all'
```

### Support for custom log from openvpnas server
To activate the log capture from openvpnas server, you will need to change the set to True the variable: ```stackdriver_openvas: True``` inside the `defautls/main.yml` file.