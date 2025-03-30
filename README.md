# Spoopy Stack Ansible Playbook

This Ansible playbook is used to configure and deploy Spoopy services across different server groups. It includes roles for common server configuration, security hardening, and service-specific deployments.

## Prerequisites

- Ansible >= 2.9.0
- Python >= 3.8
- SSH access to target servers
- Sudo privileges on target servers

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd spoopy-stack
```

2. Install required Ansible collections and roles:
```bash
ansible-galaxy install -r requirements.yml
```

3. Install pre-commit hooks (optional but recommended):
```bash
pre-commit install
```

## Configuration

1. Configure your inventory in the `inventory/` directory.

2. For convenience save the vault password in `.vault_pass` file (Optional)

## Usage

### Running the Playbook

To run the playbook against all hosts:
```bash
ansible-playbook site.yml --vault-pass-file .vault_pass --ask-become-pass
```

### Using Vault

To edit sensitive variables:
```bash
ansible-vault edit ./inventory/group_vars/buyback/vault.yml
ansible-vault edit ./inventory/group_vars/wanderer/vault.yml
```

## Playbook Structure

The playbook consists of the following main components:

- `site.yml`: Main playbook file
- `roles/`: Contains all Ansible roles
- `inventory/`: Server inventory configuration
- `requirements.yml`: External role and collection dependencies

### Host Groups

- `all`: Common configuration for all servers
- `buyback`: Buyback service deployment
- `wanderer`: Wanderer service deployment

## Roles

The playbook includes the following roles:

- `common`: Basic server configuration
- `geerlingguy.security`: Security hardening
- `geerlingguy.docker`: Docker installation and configuration
- `buyback`: Buyback service deployment
- `wanderer`: Wanderer service deployment
- `caddy`: Caddy reverse-proxy server configuration

## Development

### Code Quality

The project uses:
- `yamllint` for YAML linting
- `pre-commit` hooks for automated checks

### Testing

Before committing changes, ensure:
1. All YAML files are properly formatted
2. The playbook runs without errors
3. All sensitive data is properly encrypted

## License

MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
