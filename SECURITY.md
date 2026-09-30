# Security policy

## Reporting a vulnerability

Please do not report security problems in public issues.

Report them privately through GitHub:
[Security > Report a vulnerability](https://github.com/stackharbor-devops/seaweedfs-multi-region/security/advisories/new).
Include what an attacker could do, the affected version or commit, and steps to reproduce.
You should get a reply within a few working days.

## Scope

In scope: this package's JPS manifests, node scripts, the `sfsctl` control plane and its
web UI. For example: joining a cluster without a valid enrollment token, reaching the
management UI or API without a sign-in grant, a replayed token or grant being accepted,
a command injection through an add-on form or the API, or data readable by an
environment that was not given access.

Out of scope: vulnerabilities in SeaweedFS, nginx or the Virtuozzo Application Platform
itself. Report those to their maintainers.

## Security model, in short

The full model is in [docs/SECURITY-MODEL.md](docs/SECURITY-MODEL.md).

- Cluster traffic stays on the platform's private network, including between regions.
- SeaweedFS components talk over mutual TLS with certificates from the cluster's own
  certificate authority. Node keys are generated on the node and never leave it.
- A node joins only with a one-time enrollment token bound to its node id and IP address.
- The management UI has no permanent credentials. The dashboard's Open Advanced
  Management button mints a one-time sign-in grant, valid for 60 seconds, on the
  control-plane node. The signing secret never leaves that node.
