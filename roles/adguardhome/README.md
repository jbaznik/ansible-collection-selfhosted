# selfhosted.adguardhome

Installs [AdGuardHome](https://github.com/AdguardTeam/AdGuardHome) - a network-wide ads & trackers blocking DNS server.

> [!NOTE]
> This role is not actively maintained as it is currently not in use (since November 2024).
> Bugs may be present due to incompatibility with the latest versions of AdGuardHome image.

> [!WARNING]
> This role modifies `/etc/resolv.conf` file to bind AdGuardHome on port 53.
> See [Note on resolved daemon and adguardhome_dns_port](#note-on-resolved-daemon-and-adguardhome_dns_port).

## Role Variables

- `adguardhome_version`
  - Default: `latest`
  - Description: The version of AdGuardHome to install. See [tags](https://hub.docker.com/r/adguard/adguardhome/tags).
  - Type: str
  - Required: no
- `adguardhome_dns_port`
  - Default: `53`
  - Description: The port on which AdGuardHome will listen for DNS requests. See [docs](https://github.com/AdguardTeam/AdGuardHome/wiki/Docker#create-and-run-the-container). See [Note on resolved daemon and adguardhome_dns_port](#note-on-resolved-daemon-and-adguardhome_dns_port).
  - Type: int
  - Required: no
- `adguardhome_webui_port`
  - Default: `3000`
  - Description: The port on which AdGuardHome WebUI will be accessible.
  - Type: int
  - Required: no
- `adguardhome_install_dir`
  - Default: `/opt/docker/adguardhome`
  - Description: The directory where AdGuardHome will be installed.
  - Type: str
  - Required: no
- `adguardhome_env`
  - Default: See [adguardhome_env_default](./vars/main.yml)
  - Description: Docker container environment variables.
  - Type: dict
  - Required: no
- `adguardhome_docker_settings`
  - Default: See [adguardhome_docker_settings_default](./vars/main.yml)
  - Description: Docker container settings.
  - Type: dict
  - Required: no

## Dependencies

- [community.docker](https://docs.ansible.com/ansible/latest/collections/community/docker/index.html)

## Example Playbook

```yaml
- hosts: localhost

  roles:
    - artyorsh.selfhosted.adguardhome
``` 

## Note on resolved daemon and adguardhome_dns_port

If the system is runing resolved daemon, docker will fail to bind on port 53. For this reason a new resolv.conf file is created. See [docs](https://github.com/AdguardTeam/AdGuardHome/wiki/Docker#resolved) and [the task](./tasks/resolved.yml).