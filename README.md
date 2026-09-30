# SeaweedFS Multi-Region Storage for Jelastic / Virtuozzo

A distributed, replicated file storage platform for Virtuozzo Application Platform
(Jelastic), deployed and managed through JPS. The data plane is
[SeaweedFS](https://github.com/seaweedfs/seaweedfs). On top of it the package adds its own
control plane: secure node enrollment, automatic rebalancing and healing, replication
between regions, backups, health monitoring, and a management UI opened from the
dashboard with single sign-on.

The goal is simple scaling: deploy a storage cluster, then add nodes and regions and let
the platform handle the rest.

This is a separate option alongside
[glusterfs-multi-region](https://github.com/stackharbor-devops/glusterfs-multi-region), not a
replacement for it. GlusterFS gives one synchronously replicated volume stretched across
regions. This platform keeps one cluster per region that grows with every node added, with
asynchronous replication between regions.

> **Status: v0 preview, under review in a pull request.** Tested locally only. Not yet
> installed on a live Jelastic platform.

## License & contribution

MIT, see [LICENSE](LICENSE). Bug reports, test results, ideas and pull requests are
welcome: see [CONTRIBUTING.md](CONTRIBUTING.md). File bugs and feature requests at
<https://github.com/stackharbor-devops/seaweedfs-multi-region/issues>. Report security
problems privately, as described in [SECURITY.md](SECURITY.md).
