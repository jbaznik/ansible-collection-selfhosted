# selfhosted.paperless_ai

Installs [paperless-ai](https://github.com/clusterzx/paperless-ai) - an automated document analyzer for Paperless-ngx using OpenAI API, Ollama and all OpenAI API compatible LLMs.

## Requirements

- [Paperless-ngx](../paperlessngx/README.md)
- [OpenAI API key](https://platform.openai.com/settings/organization/api-keys) in case not running local LLMs.

## Role Variables

- `paperless_ai_version`
  - Default: `latest`
  - Description: The version of paperless-ai to install. See [docker tags](https://hub.docker.com/r/clusterzx/paperless-ai/tags).
  - Type: str
  - Required: no
- `paperless_ai_port`
  - Default: `3000`
  - Description: The port on which paperless-ai will be accessible.
  - Type: int
  - Required: no
- `paperless_ai_docker_settings`
  - Default: See [paperless_ai_docker_settings_default](./vars/main.yml)
  - Description: Docker container settings.
  - Type: dict
  - Required: no
- `paperless_ai_install_dir`
  - Default: `/opt/docker/paperless-ai`
  - Description: The directory where paperless-ai will be installed.
  - Type: str
  - Required: no
- `paperless_ai_env`
  - Default: See [paperless_ai_env_default](./vars/main.yml)
  - Description: Docker container environment variables. See [.env.example](https://github.com/clusterzx/paperless-ai/blob/main/.env.example).
  - Type: dict
  - Required: no

## Dependencies

- [community.docker](https://docs.ansible.com/ansible/latest/collections/community/docker/index.html)

## Example Playbook

```yaml
- hosts: localhost

  roles:
    - artyorsh.selfhosted.paperless_ai
```

### Install with paperlessngx

Paperless-AI requires API access to Paperless-NGX. After the installation, visit the {{ paperlessngx_url}}/admin/authtoken/tokenproxy to create one.

```yaml
- hosts: localhost

  roles:
    - artyorsh.selfhosted.paperlessngx
    - artyorsh.selfhosted.paperless_ai
```
