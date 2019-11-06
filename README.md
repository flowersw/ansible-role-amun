Thoth: Amun
===========

This role will deploy all Amun components to a given OpenShift Project.

Role Variables
--------------

This role requires a few variables:

```
AMUN_INFRA_NAMESPACE: "<namespace containing the templates>"
AMUN_API_NAMESPACE: "<namespace hosting the amun api>"
AMUN_INSPECTION_NAMESPACE: "<namespace for running the inspection jobs>"
AMUN_API_APP_SECRET_KEY: "<Amun API key>"
PROMETHEUS_PUSHGATEWAY_HOST: "<Prometheus host>"
PROMETHEUS_PUSHGATEWAY_PORT: "<Pormetheus port>"
SENTRY_DSN: "<Sentry DSN>"
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters):

```yaml
- hosts: localhost
  connection: local
  gather_facts: False

  # additional variables
  vars:
    # Defaults to the SA specified in amunInspectionNamespace-template
    SERVICE_ACCOUNT_NAME: "inspector"
    # Image registry specific to the cluster (by default for OpenShift)
    # for minishift use <host>:5000, e.g. 172.30.1.1:5000
    IMAGE_REGISTRY: docker-registry.default.svc:5000

  roles:
    - role: thoth-station.anum
      AMUN_INFRA_NAMESPACE: "thoth-test-core"
      AMUN_API_NAMESPACE: "thoth-test-core"
      AMUN_INSPECTION_NAMESPACE: "thoth-test-core"
      AMUN_API_APP_SECRET_KEY: "{{ lookup('env','AMUN_API_APP_SECRET_KEY') }}"
      PROMETHEUS_PUSHGATEWAY_HOST: "{{ lookup('env','PROMETHEUS_PUSHGATEWAY_HOST') }}"
      PROMETHEUS_PUSHGATEWAY_PORT: "{{ lookup('env','PROMETHEUS_PUSHGATEWAY_PORT') }}"
      SENTRY_DSN: "{{ lookup('env','SENTRY_DSN') }}"
```yaml

License
-------

GPLv3

Author Information
------------------

The Thoth Station Team.