# Ansible Playbooks — Infrastructure Automation

Operational Ansible playbooks used in production environments.
Covers service deployment, Docker lifecycle management,
and monitoring agent operations.

## Playbooks

### Monitoring agent (c-agent)
Custom metric collector for storage and infrastructure monitoring.

| Playbook | Description |
|---|---|
| `install-c-agent.yml` | Fresh install with config |
| `update_c-agent.yml` | Update with config reload |
| `update_c-agent_without_conf.yml` | Binary update, preserve config |
| `update_c-agent_config.yml` | Config update without restart |
| `restart_c-agent.yml` | Graceful restart |
| `stop_c-agent.yml` | Stop agent |

### Docker management

| Playbook | Description |
|---|---|
| `docker_container_list.yml` | Inventory running containers |
| `docker_container_start.yml` | Start target container |
| `docker_container_stop.yml` | Stop target container |
| `docker_container_restart.yml` | Restart target container |
| `interactive_docker.yml` | Interactive container operations |

### Service deployment

| Playbook | Description |
|---|---|
| `service_deploy.yml` | Generic service deployment |
| `deploy_metric-collector.yml` | Deploy full monitoring stack |
| `deploy_gitlab.yml` | GitLab instance deployment |
| `gitlab_runners_deploy.yml` | GitLab CI runners deployment |

## Usage

```bash
# Install monitoring agent on target hosts
ansible-playbook playbook-roles/playbooks/install-c-agent.yml \
  -i inventory/hosts.yml

# Update agent preserving existing config
ansible-playbook playbook-roles/playbooks/update_c-agent_without_conf.yml \
  -i inventory/hosts.yml --limit production
```

## Structure
