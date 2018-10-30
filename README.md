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
```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters):

    - hosts: localhost
      connection: local
      gather_facts: False

      roles:
        - role: thoth-station.anum
          AMUN_INFRA_NAMESPACE: "thoth-test-core"
          AMUN_API_NAMESPACE: "thoth-test-core"
          AMUN_INSPECTION_NAMESPACE: "thoth-test-core"

License
-------

GPLv3

Author Information
------------------

The Thoth Station Team.