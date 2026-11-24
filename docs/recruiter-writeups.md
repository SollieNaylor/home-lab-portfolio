# Recruiter-facing summaries

These are draft descriptions for a personal portfolio. Use them only if the related results have been confirmed.

## Project 01 — Linux Server Administration

**Short description:** Built a virtualized Ubuntu Server lab on a Linux Mint workstation using KVM/QEMU and libvirt; configured remote SSH administration, basic firewall rules, and an Nginx-hosted test webpage.

**Resume bullet:** Built and administered a virtualized Ubuntu Server environment using KVM/QEMU, SSH key-based access, UFW host firewall policies, and Nginx web hosting to practice Linux and network administration.

**Interview talking points:** Why NAT was chosen over bridged networking; distinction between host and guest; how an absent SSH service differs from an authentication denial; how firewall rules relate to service ports.

## Project 02 — Ansible Automation

**Short description:** Developed an Ansible control-node workflow for a virtual Ubuntu web server, including a working inventory and remote module execution; prepared an Nginx configuration playbook to manage software, services, and web content.

**Resume bullet (use after confirming successful playbook deployment):** Automated Ubuntu web server configuration with Ansible YAML playbooks, managing Nginx package state, systemd service availability, and HTML content over SSH.

**Resume bullet (already validated):** Configured Ansible inventory and SSH-based access to a Linux VM, troubleshooting inventory parsing and Python interpreter discovery before validating remote execution with `ansible.builtin.ping`.

**Interview talking points:** Why inventory is separate from playbooks; `become: true`; how Ansible modules maintain state; interpreting `ok`, `changed`, and `failed`; why the second run matters.

## Writing standards

- Do not claim enterprise scale, production uptime, reduced costs, performance improvements, or cloud integrations without measured evidence.
- Use 'personal home lab' where helpful so employers understand the context.
- Present mistakes as debugging lessons, not as production incidents.
- Add screenshots and actual outcomes before treating an unverified step as finished.
