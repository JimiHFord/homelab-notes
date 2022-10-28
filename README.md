# [Proxmox](https://www.proxmox.com/en/proxmox-ve)

`nuke-cluster.sh`
```bash
systemctl stop pve-cluster corosync
pmxcfs -l
rm -rf /etc/corosync/*
rm /etc/pve/corosync.conf
killall pmxcfs
systemctl start pve-cluster
```

[Proxmox Tools](https://tteck.github.io/Proxmox/)

# Future Services

## [PeerTube](https://github.com/Chocobozzz/PeerTube)

## [Nextcloud](https://github.com/nextcloud)

## [OpenStack](https://www.openstack.org/)

## [Element](https://element.io/)

## [GitLab](https://about.gitlab.com/install/)

## [Gitea](https://github.com/go-gitea/gitea)

## [Pi-hole](https://pi-hole.net/)

## [Portainer](https://www.portainer.io/)

## [Rancher](https://rancher.com/)

## [Plex](https://www.plex.tv/)

## [Jellyfin](https://jellyfin.org/)

## [pfsense](https://www.pfsense.org/)

## [OpnSense](https://opnsense.org/)

## [BitWarden](https://bitwarden.com/)

## [OnlyOffice](https://www.onlyoffice.com/desktop.aspx?AFFILIATE=6732&__c=1&affChecked=1)

## [Joplin](https://joplinapp.org/)

## [Taiga](https://www.taiga.io/)

## [Duplicati](https://www.duplicati.com/)

## [TrueNAS](https://www.truenas.com/)

## [Docker Mailserver](https://github.com/docker-mailserver/docker-mailserver)

## [Matomo](https://github.com/matomo-org/matomo)

## [IdentityServer](https://github.com/IdentityServer)

## [Excalidraw](https://github.com/excalidraw/excalidraw)

## [JupyterHub](https://jupyter.org/hub)

## [Sourcegraph](https://github.com/sourcegraph/sourcegraph)

## [Hydra](https://github.com/ory/hydra)

## [Cockpit](https://cockpit-project.org/)

## [mailtrain](https://github.com/Mailtrain-org/mailtrain)

## [sendportal](https://github.com/mettle/sendportal)

## [listmonk](https://listmonk.app/docs/)

## [Datree](https://github.com/datreeio/datree)

## [Prometheus](https://prometheus.io/)

## [Grafana](https://grafana.com/)

## [Searx](https://www.youtube.com/watch?v=ifT6npY39Dw)

...and more from [this article](https://aaron-kt-berry.medium.com/top-10-software-for-your-homelab-in-2021-98137a7de051)


# Future Projects

[ModelZoo](https://modelzoo.co/)

[Ceph](https://www.reddit.com/r/homelab/comments/8f6tdg/anybody_having_ceph_builds_in_their_homelab/)

[SageMath](https://www.sagemath.org/)

[GNU Octave](https://www.gnu.org/software/octave/)

[RAUC](https://github.com/rauc/rauc)

[Photo Prism](https://photoprism.app/)

[25 Open Datasets](https://www.analyticsvidhya.com/blog/2018/03/comprehensive-collection-deep-learning-datasets/)

## Approach notes

Start with OKD and build around that
Don't exclude virting in favor of containers - recipe for bad architecture

S4E

storage:
estimate starting at 24TB
options:
* storage and compute on same machine
* storage on 1 machine compute on the other

go with second option

hyperconverge
rook configue ceph with 

