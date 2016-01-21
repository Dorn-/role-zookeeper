# Role Zookeeper

Role d'installation de Zookeeper.

Zookeeper est un manager de cluster, utilisé entre autres par SolrCloud.

## Changelog

Révision initiale

## Variables

### Defaults
`zookeeper_cluster_group`: nom du groupe Ansible contenant les membres
du cluster (default: false, *obligatoire*)
`zookeeper_connection_port`: port de connexion à zookeeper (default:
2888)
`zookeeper_election_port`: port pour les élections du cluster (default:
3888)

### Vars

`zookeeper_datadir`: data directory pour zookeeper (default: /data/zookeeper/)
`zookeeper_download_url`: URL de téléchargement de zookeeper (default:
http://apache.crihan.fr/dist/zookeeper/zookeeper-3.4.6/zookeeper-3.4.6.tar.gz)
`zookeeper_install_dir`: (default: /srv/zookeeper)

