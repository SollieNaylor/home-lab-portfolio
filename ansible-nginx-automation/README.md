# Project 02 — Automating a Linux Web Server with Ansible

## Executive summary

Created an Ansible inventory and used the Linux Mint workstation as the control node to administer an Ubuntu Server virtual machine (`lab01`) over SSH. The inventory was validated when Ansible returned `SUCCESS` with `ping: pong`; an Nginx management playbook was then prepared and the deployment was reported complete. Repeatability (`changed=0` on the second run) still needs a captured verification result.

## Goals

- Manage Ubuntu remotely from a separate Linux control node.
- Use YAML playbooks to declare the desired Nginx package and service state.
- Deploy web content using a repeatable task.
- Verify idempotency with a second playbook run.

## Architecture

```mermaid
flowchart LR
  M[Linux Mint control node] -->|SSH, ED25519 key| U[Ubuntu lab01]
  P[nginx.yml playbook] --> M
  U --> N[Nginx service + HTML page]
```

## Implementation

1. Prepared a Linux Mint control node with Ansible Core.
2. Created a `[webservers]` inventory group for the Ubuntu VM.
3. Fixed an initial inventory parsing issue by correcting the INI inventory format and host definition.
4. Loaded an existing ED25519 private key on the control node using `ssh-add`.
5. Validated remote management with `ansible -i inventory.ini webservers -m ansible.builtin.ping`.
6. Prepared an Ansible playbook that installs Nginx, ensures it is running/enabled, and deploys a custom HTML page.
7. Reported completing the playbook exercise. A sanitized run recap and second-run result still need to be captured.

## Actual connectivity evidence (sanitized excerpt)

```text
[WARNING]: Host 'lab01' is using the discovered Python interpreter at '/usr/bin/python3.14' ...
lab01 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3.14"
    },
    "changed": false,
    "ping": "pong"
}
```

This proves Ansible reached the guest, authenticated, and executed its Python-based module. It does **not** on its own establish that the Nginx playbook ran successfully.

## Files

- [`playbooks/nginx.yml`](playbooks/nginx.yml) — clean reference playbook based on the lab exercise. Compare with your deployed `~/homelab/ansible/nginx.yml` before claiming it is byte-for-byte the deployed version.
- [`inventory.example.ini`](inventory.example.ini) — shareable sample; never publish `inventory.ini` containing live connection details or credentials.

## Troubleshooting and decisions

**Inventory parsing failure:** Ansible initially warned that no inventory could be parsed and that the `webservers` group was missing. Correcting the inventory entry resulted in a successful remote ping.

**SSH key added on wrong machine:** `ssh-add` failed on the remote Ubuntu VM because the key belonged to the Linux Mint control node. Running `ssh-add ~/.ssh/ubuntu_lab_ed25519` on Linux Mint succeeded.

**Python discovery warning:** Ansible discovered `/usr/bin/python3.14`. This did not prevent the ping. An explicitly selected interpreter can avoid future ambiguity once verified.

**Package specification troubleshooting:** An earlier attempt to install a version-pinned Ansible package produced a spec-parsing error; the exact resolution was not recorded. Avoid asserting it was fixed by a particular command without evidence.

## Validation checklist

- [x] Ansible inventory accepted and host reachable.
- [x] `ansible.builtin.ping` returned `SUCCESS` and `pong`.
- [x] User reported completion of the Nginx playbook exercise.
- [ ] Preserve a sanitized `ansible-playbook --syntax-check` result.
- [ ] Preserve a successful first-run `PLAY RECAP` with `failed=0`.
- [ ] Run a second time and record `changed=0` if reproducible.
- [ ] Capture a screenshot of the page after Ansible deployed it.

## Demonstrated skills

Inventory modeling, key-based SSH, Linux control/managed nodes, Ansible modules (`apt`, `service`, `copy`), YAML playbook structure, troubleshooting remote Python, and testing desired configuration state.

## Future improvement

Move HTML into a Jinja2 template, add handlers for service reloads, introduce `ansible-lint`, and write a separate playbook for firewall rules with safe order of operations.
