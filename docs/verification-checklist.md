# Publication verification checklist

Keep all portfolio claims aligned with observable evidence.

## Confirmed by terminal output supplied during the lab

- [x] Linux Mint host uses kernel `6.14.0-37-generic` and Cinnamon 6.6.9 on Mint 22.3.
- [x] Dell OptiPlex 9020 motherboard `0XCR8D`, i7-4770, 16 GiB RAM, `P3-512` system drive.
- [x] VT-x present in `lscpu`; `/dev/kvm` exists.
- [x] SSH key loaded on Linux Mint with `ssh-add` (`Identity added`).
- [x] Ansible reached `lab01`; `SUCCESS` and `ping: pong` shown.
- [x] Remote Ansible interpreter auto-detected as `/usr/bin/python3.14`.

## Reported complete in conversation, supporting logs still to collect

- [ ] Ubuntu guest installation and exact version (`cat /etc/os-release`).
- [ ] SSH access with key (capture `ssh -v` summary or login without sharing secrets).
- [ ] UFW rules active (`sudo ufw status verbose`).
- [ ] Nginx service active and sample page reachable.
- [ ] Ansible playbook syntax check, deployment success, and `changed=0` on repeat run.
- [ ] Git initialized and commit history published (not yet confirmed).

## Suggested safe evidence collection commands

Run on Ubuntu VM:

```bash
cat /etc/os-release
systemctl is-active ssh nginx
sudo ufw status verbose
```

Run on Linux Mint host:

```bash
lscpu | grep Virtualization
ls -l /dev/kvm
ansible --version
ansible-inventory -i ~/homelab/ansible/inventory.ini --graph
cd ~/homelab/ansible
ansible-playbook -i inventory.ini nginx.yml --syntax-check
ansible-playbook -i inventory.ini nginx.yml -K
```

To test idempotency, run the same playbook a second time and compare recaps. Capture only sanitized output; never include passwords, private keys, or auth tokens.
