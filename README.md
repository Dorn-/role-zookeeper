# Role Ansible Zookeeper

## Warning/Requirement
*No comment*
 
## Role Variables
### Mandatory
- `zookeeper_cluster_group`: nom du groupe Ansible contenant les membres du cluster (default: false)
- `zookeeper_cluster_interface`: (default: false)

### Optional
- `zookeeper_client_port`: (default: 2181)
- `zookeeper_connection_port`: port de connexion à zookeeper (default:2888)
- `zookeeper_election_port`: port pour les élections du cluster (default:3888)
- `zookeeper_datadir`: data directory pour zookeeper (default: /data/zookeeper/)
- `zookeeper_download_url`: URL de téléchargement de zookeeper (default:http://apache.crihan.fr/dist/zookeeper/zookeeper-3.4.6/zookeeper-3.4.6.tar.gz)
- `zookeeper_install_dir`: (default: /srv/zookeeper)

## Tags
*No comment*

## Dependencies
*No comment*

## Changelog
[2.0.0](CHANGELOG.md)

## Notes/Examples
Role d'installation de Zookeeper.
Zookeeper est un manager de cluster, utilisé entre autres par SolrCloud.

## Licence
[MIT License](http://www.opensource.org/licenses/MIT)
>>>>>>> develop

## Author Information
@m-blanc
@f-chantelot
