# Ansible Role: EPICS StreamDevice

Installs EPICS StreamDevice on RHEL/CentOS.

## Requirements

- ansible >= 2.3

## Role Variables
Refer to `defaults/main.yml` in detail.
```
epics_stream_module:
  name: "stream"
  type: "soft"
  ver: "2_7_7"
  url: "https://github.com/paulscherrerinstitute/StreamDevice"
  configure_release:
      - {name: "EPICS_BASE", path: "{{ epics_base_base_name }}", reg: "^(.*)EPICS_BASE(.*)=(.*)$"}
      - {name: "SNCSEQ", path: "{{ epics_base_modules_name }}/soft/seq/{{ epics_seq_module.ver }}", reg: "^(.*)SNCSEQ(.*)=(.*)$"}
      - {name: "ASYN", path: "{{ epics_base_modules_name }}/soft/asyn/{{ epics_asyn_module.ver }}", reg: "^(.*)ASYN(.*)=(.*)$"}
```

## Dependencies

- [ansible-role-epics-base](https://github.com/sasaki77/ansible-role-epics-base)
- [ansible-role-epics-seq](https://github.com/sasaki77/ansible-role-epics-seq)
- [ansible-role-epics-asyn](https://github.com/sasaki77/ansible-role-epics-asyn)

## Example Playbook
```
- hosts: epics-base
  roles:
    - role: ansible-role-epics-base
    - role: ansible-role-epics-seq
    - role: ansible-role-epics-asyn
    - role: ansible-role-epics-stream
```

## License

None.

## Author Information

This role was created by Shinya Sasaki.
