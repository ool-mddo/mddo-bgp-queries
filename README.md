# mddo-bgp-queries

Batfish出力サンプル (参照用)

## Target Network
* [mddo-bgp network](https://github.com/ool-mddo/mddo-bgp) 参照

## Batfish Query
* [batfish-wrapper](https://github.com/ool-mddo/batfish-wrapper) (詳細は[bf_query_thrower.py](https://github.com/ool-mddo/batfish-wrapper/blob/main/src/bfwrapper/bf_query_thrower.py)) 参照

|Target|Query|Output|Note|
|------|-----|------|----|
|IP設定情報|[ip_owners](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#IP-Owners)|[ip_owners.csv](./original_asis/ip_owners.csv)||
|インタフェース設定|[interface_props](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#Interface-Properties)|[interface_props.csv](./original_asis/interface_props.csv)|一部の列のみ取得|
|ノード設定|[node_props](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#Node-Properties)|[node_props.csv](./original_asis/node_props.csv)||
|VLANパラメタ|[sw_vlan_props](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#VLAN-Properties)|[sw_vlan_props.csv](./original_asis/sw_vlan_props.csv)||
|OSPFプロセス設定|[ospf_proc_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#OSPF-Process-Configuration)|[ospf_proc_conf.csv](./original_asis/ospf_proc_conf.csv)||
|OSPFインタフェース設定|[ospf_intf_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#OSPF-Interface-Configuration)|[ospf_intf_conf.csv](./original_asis/ospf_intf_conf.csv)||
|OSPFエリア設定|[ospf_area_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#OSPF-Area-Configuration)|[ospf_area_conf.csv](./original_asis/ospf_area_conf.csv)||
|BGPプロセス設定|[bgp_proc_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#BGP-Process-Configuration)|[bgp_proc_conf.csv](./original_asis/bgp_proc_conf.csv)||
|BGPピア設定|[bgp_peer_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#BGP-Peer-Configuration)|[bgp_peer_conf.csv](./original_asis/bgp_peer_conf.csv)||
|経路情報(静的経路)|[routes](https://pybatfish.readthedocs.io/en/latest/notebooks/routingTables.html#Routes)|[routes.csv](./original_asis/routes.csv)||
|名前付きオブジェクト|[named_structures](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#Named-Structures)|[named_structures.csv](./original_asis/named_structures.csv)||

