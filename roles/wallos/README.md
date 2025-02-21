# selfhosted.wallos

Installs [wallos](https://github.com/ellite/Wallos/pkgs/container/wallos) - an Open-Source Personal Subscription Tracker.

## Role Variables

- `wallos_version`
  - Default: `latest`
  - Description: The version of wallos to install. See [tags](https://github.com/ellite/Wallos/pkgs/container/wallos)
  - Type: str
  - Required: no
- `wallos_install_dir`
  - Default: `/opt/docker/wallos`
  - Description: The directory where wallos will be installed.
  - Type: str
  - Required: no
- `wallos_webui_port`
  - Default: `8282`
  - Description: The port on which the wallos web UI will be accessible.
  - Type: int
  - Required: no
- `wallos_env`
  - Default: See [wallos_env_default](./vars/main.yml)
  - Description: Docker container environment variables.
  - Type: dict
  - Required: no
- `wallos_docker_settings`
  - Default: See [wallos_docker_settings_default](./vars/main.yml)
  - Description: Docker container settings.
  - Type: dict
  - Required: no

## Dependencies

- [community.docker](https://docs.ansible.com/ansible/latest/collections/community/docker/index.html)

## Example Playbook

```yaml
- hosts: localhost

  roles:
    - artyorsh.selfhosted.wallos
```