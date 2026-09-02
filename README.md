# Cloud Provider Collection for GCP — AgnosticD V2

Ansible collection providing GCP infrastructure provisioning roles for
[AgnosticD V2](https://github.com/rhpds/agnosticd-v2).

Follows the same architecture as
[cloud_provider_aws](https://github.com/rhpds/cloud_provider_aws):
thin in-tree playbooks under `agnosticd-v2/ansible/cloud_providers/gcp/`
call these roles via FQCN (`agnosticd.cloud_provider_gcp.<role>`).

## Roles

| Role | Purpose |
|------|---------|
| `credentials_file` | Write GCP service account JSON to output directory |
| `install_sdk` | Install Google Cloud SDK on bastion host |
| `open_environment` | Add user IAM bindings to a GCP Open Environment project |
| `ssh_key` | Create and manage SSH metadata keys in GCP |
| `user_info` | Report GCP access information via `agnosticd_user_info` |
| `create_network` | Create VPC, subnets, firewall rules, Cloud NAT, Cloud Router |
| `create_instances` | Create GCE VM instances (bastion + optional workers) |
| `create_inventory` | Build Ansible inventory from GCE instances |
| `destroy_instances` | Delete GCE VM instances |
| `destroy_network` | Delete VPC, subnets, firewall rules |
| `dns` | Create and delete Cloud DNS records |
| `detect_region` | Determine GCP region from existing resources |
| `lifecycle` | Stop, start, and query status of GCE instances |
| `wait_for_linux_hosts` | Wait for SSH readiness on GCE instances |
| `linux_set_hostname` | Set hostname on GCE Linux instances |

## Requirements

- `google.cloud` Ansible collection >= 1.0.0
- `gcloud` CLI (installed by the `install_sdk` role when absent)
- GCP service account with project-level permissions

## Installation

The collection is installed automatically by AgnosticD V2 when
`cloud_provider: gcp` is set in the vars file. Manual install:

```bash
ansible-galaxy collection install git+https://github.com/tosin2013/cloud_provider_gcp.git
```

## License

Apache-2.0
