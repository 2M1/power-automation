# power-automation

Ansible automation for Power Autonomous Operations.

## Structure

```
power-automation/
├── playbooks/
│   ├── collect_logs.yml   # Collect logs via HMC
│   ├── resize_lpar.yml    # Resize LPAR CPU/memory via HMC
│   └── healthcheck.yml    # Health checks on Power systems
├── roles/
│   ├── power_health/      # Health check tasks
│   └── hmc_operations/    # HMC operations (collect_logs, resize_lpar)
├── inventories/
│   └── production         # Production inventory (groups: hmc, power)
├── group_vars/
├── host_vars/
└── README.md
```

## Usage

```bash
ansible-playbook -i inventories/production playbooks/healthcheck.yml
ansible-playbook -i inventories/production playbooks/collect_logs.yml
ansible-playbook -i inventories/production playbooks/resize_lpar.yml \
  -e lpar_name=<name> -e managed_system=<system>
```

## Security

Never commit credentials. Use Ansible Vault or an external secrets manager
for HMC and host credentials.

## Status

Playbooks and roles are skeletons; task logic still needs to be implemented.
