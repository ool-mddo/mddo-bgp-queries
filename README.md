# mddo-bgp-queries

Batfish/BGP Policy 出力サンプル (参照/デモ説明用)
* See also: [システムコンポーネントとその関係](https://github.com/ool-mddo/playground/blob/main/doc/system_architecture.md#システムコンポーネントとその関係)

## Target Network (Input data)

[mddo-bgp network](https://github.com/ool-mddo/mddo-bgp) 参照
- [Network device configs](https://github.com/ool-mddo/mddo-bgp/tree/main/original_asis/configs)
- [Layer1 topology](https://github.com/ool-mddo/mddo-bgp/blob/main/original_asis/batfish/layer1_topology.json)
  - See also: [物理トポロジデータの生成と編集](https://github.com/ool-mddo/playground/blob/main/demo/layer1_topology/README.md)

## Batfish Query (Intermediate output)

[batfish-wrapper](https://github.com/ool-mddo/batfish-wrapper) (詳細は[bf_query_thrower.py](https://github.com/ool-mddo/batfish-wrapper/blob/main/src/bfwrapper/bf_query_thrower.py)) 参照

|Target|Query|Output|Note|
|------|-----|------|----|
|IP設定情報|[ip_owners](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#IP-Owners)|[ip_owners.csv](./configs/ip_owners.csv)||
|インタフェース設定|[interface_props](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#Interface-Properties)|[interface_props.csv](./configs/interface_props.csv)|一部の列のみ取得|
|ノード設定|[node_props](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#Node-Properties)|[node_props.csv](./configs/node_props.csv)||
|VLANパラメタ|[sw_vlan_props](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#VLAN-Properties)|[sw_vlan_props.csv](./configs/sw_vlan_props.csv)||
|OSPFプロセス設定|[ospf_proc_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#OSPF-Process-Configuration)|[ospf_proc_conf.csv](./configs/ospf_proc_conf.csv)||
|OSPFインタフェース設定|[ospf_intf_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#OSPF-Interface-Configuration)|[ospf_intf_conf.csv](./configs/ospf_intf_conf.csv)||
|OSPFエリア設定|[ospf_area_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#OSPF-Area-Configuration)|[ospf_area_conf.csv](./configs/ospf_area_conf.csv)||
|BGPプロセス設定|[bgp_proc_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#BGP-Process-Configuration)|[bgp_proc_conf.csv](./configs/bgp_proc_conf.csv)||
|BGPピア設定|[bgp_peer_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#BGP-Peer-Configuration)|[bgp_peer_conf.csv](./configs/bgp_peer_conf.csv)||
|経路情報|[routes](https://pybatfish.readthedocs.io/en/latest/notebooks/routingTables.html#Routes)|[routes.csv](./configs/routes.csv)|local,staticのみ参照|
|名前付きオブジェクト|[named_structures](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#Named-Structures)|[named_structures.csv](./configs/named_structures.csv)|BGPポリシの名前取得で利用|

当初L1/L3トポロジ情報 ([layer1_edges](https://pybatfish.readthedocs.io/en/latest/notebooks/topology.html#User-Provided-Layer-1-Topology), [layer3_edges](https://pybatfish.readthedocs.io/en/latest/notebooks/topology.html#Layer-3-Topology))も参照していましたが interface description 定義ベースのトポロジ管理に移行したので現在は使用していません。

トポロジ情報については[mddo-bgp network](https://github.com/ool-mddo/mddo-bgp)同梱の[トポロジデータ(layer1_topoollgy.json)](https://github.com/ool-mddo/mddo-bgp/blob/main/original_asis/batfish/layer1_topology.json)を参照。これは、interface description の情報→netbox→batfishインプット用のL1トポロジとして出力したものです。詳細は[playground](https://github.com/ool-mddo/playground/tree/main)にある、[物理トポロジデータの生成](https://github.com/ool-mddo/playground/blob/main/demo/layer1_topology/doc/operation.md)を参照してください。

## BGP Policy (Intermediate output)

BGPポリシ(ルール本体)のデータ取得についてはBatfishを利用せず[独自parser(bgp-policy-parser)](https://github.com/ool-mddo/bgp-policy-parser)を使用しています。

出力サンプル
* TTPによる中間出力(ベンダ依存)
  * [Cisco系](./ttp_outputs/cisco_ios_xr/)
  * [Juniper系](./ttp_outputs/juniper/)
* [標準化した最終的な出力](./ttp_outputs/bgp_policies/)

## Topology (Output data)
- [topology.json](./topology/topology.json)
  - See also: [ネットワークのモデル](https://github.com/ool-mddo/playground/blob/main/doc/network_model.md)
