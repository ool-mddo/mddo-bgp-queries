# mddo-bgp-queries

Batfish/BGP Policy 出力サンプル (参照/デモ説明用)
* See also: [システムコンポーネントとその関係](https://github.com/ool-mddo/playground/blob/main/doc/system_architecture.md#システムコンポーネントとその関係)

## mddo-bgp

### Configuration (Input)

[mddo-bgp network](https://github.com/ool-mddo/mddo-bgp) 参照
- [Network device configs](https://github.com/ool-mddo/mddo-bgp/tree/main/original_asis/configs)
- [Layer1 topology](https://github.com/ool-mddo/mddo-bgp/blob/main/original_asis/batfish/layer1_topology.json)
  - See also: [物理トポロジデータの生成と編集](https://github.com/ool-mddo/playground/blob/main/demo/layer1_topology/README.md)

### Queries (Intermediate output)

[batfish-wrapper](https://github.com/ool-mddo/batfish-wrapper) (詳細は[bf_query_thrower.py](https://github.com/ool-mddo/batfish-wrapper/blob/main/src/bfwrapper/bf_query_thrower.py)) 参照

|Target|Query|Output|Note|
|------|-----|------|----|
|IP設定情報|[ip_owners](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#IP-Owners)|[ip_owners.csv](./queries/mddo-bgp/original_asis/ip_owners.csv)||
|インタフェース設定|[interface_props](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#Interface-Properties)|[interface_props.csv](./queries/mddo-bgp/original_asis/interface_props.csv)|一部の列のみ取得|
|ノード設定|[node_props](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#Node-Properties)|[node_props.csv](./queries/mddo-bgp/original_asis/node_props.csv)||
|VLANパラメタ|[sw_vlan_props](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#VLAN-Properties)|[sw_vlan_props.csv](./queries/mddo-bgp/original_asis/sw_vlan_props.csv)||
|OSPFプロセス設定|[ospf_proc_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#OSPF-Process-Configuration)|[ospf_proc_conf.csv](./queries/mddo-bgp/original_asis/ospf_proc_conf.csv)||
|OSPFインタフェース設定|[ospf_intf_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#OSPF-Interface-Configuration)|[ospf_intf_conf.csv](./queries/mddo-bgp/original_asis/ospf_intf_conf.csv)||
|OSPFエリア設定|[ospf_area_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#OSPF-Area-Configuration)|[ospf_area_conf.csv](./queries/mddo-bgp/original_asis/ospf_area_conf.csv)||
|BGPプロセス設定|[bgp_proc_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#BGP-Process-Configuration)|[bgp_proc_conf.csv](./queries/mddo-bgp/original_asis/bgp_proc_conf.csv)||
|BGPピア設定|[bgp_peer_conf](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#BGP-Peer-Configuration)|[bgp_peer_conf.csv](./queries/mddo-bgp/original_asis/bgp_peer_conf.csv)||
|経路情報|[routes](https://pybatfish.readthedocs.io/en/latest/notebooks/routingTables.html#Routes)|[routes.csv](./queries/mddo-bgp/original_asis/routes.csv)|local,staticのみ参照|
|名前付きオブジェクト|[named_structures](https://pybatfish.readthedocs.io/en/latest/notebooks/configProperties.html#Named-Structures)|[named_structures.csv](./queries/mddo-bgp/original_asis/named_structures.csv)|BGPポリシの名前取得で利用|

当初L1/L3トポロジ情報 ([layer1_edges](https://pybatfish.readthedocs.io/en/latest/notebooks/topology.html#User-Provided-Layer-1-Topology), [layer3_edges](https://pybatfish.readthedocs.io/en/latest/notebooks/topology.html#Layer-3-Topology))も参照していましたが interface description 定義ベースのトポロジ管理に移行したので現在は使用していません。

トポロジ情報については[mddo-bgp network](https://github.com/ool-mddo/mddo-bgp)同梱の[トポロジデータ(layer1_topoollgy.json)](https://github.com/ool-mddo/mddo-bgp/blob/main/original_asis/batfish/layer1_topology.json)を参照。これは、interface description の情報→netbox→batfishインプット用のL1トポロジとして出力したものです。詳細は[playground](https://github.com/ool-mddo/playground/tree/main)にある、[物理トポロジデータの生成](https://github.com/ool-mddo/playground/blob/main/demo/layer1_topology/doc/operation.md)を参照してください。

### BGP Policy (Intermediate output)

BGPポリシ(ルール本体)のデータ取得についてはBatfishを利用せず[独自parser(bgp-policy-parser)](https://github.com/ool-mddo/bgp-policy-parser)を使用しています。

出力サンプル
* TTPによる中間出力(ベンダ依存)
  * [Cisco系](./ttp/outputs/mddo-bgp/original_asis/cisco_ios_xr/)
  * [Juniper系](./ttp/outputs/mddo-bgp/original_asis/juniper/)
* [標準化した最終的な出力](./ttp/bgp_policies/mddo-bgp/original_asis/)

### Topology (Output data)
- [topology.json](./topology/mddo-bgp/original_asis/topology.json)
  - See also: [ネットワークのモデル](https://github.com/ool-mddo/playground/blob/main/doc/network_model.md)

## mddo-ospf

### Configuration (input)

[mddo-ospf](https://github.com/ool-mddo/mddo-ospf)参照
- See also: [デモ:セグメント移転ユースケース](https://github.com/ool-mddo/playground/blob/main/demo/copy_to_emulated_env/doc/move_seg/introduction.md)

### Queries (Intermediate output)

- [queries](./queries/mddo-ospf/original_asis/)

### Topology (Output data)

- [topology](./topology/mddo-ospf/original_asis/topology.json)

## pushed-configs

### Configuration (Input)

[pushed_configs](https://github.com/ool-mddo/pushed_configs)参照
- 検証用のトポロジをブランチで管理しています。ここにあるのは [202202demo2](https://github.com/ool-mddo/pushed_configs/tree/202202demo2)ブランチのコンフィグをもとにしたものです。
- See also: [リンクダウンシミュレーション](https://github.com/ool-mddo/playground/blob/main/demo/linkdown_simulation/README.md)

### Queries (Intermediate output)

- [queries](./queries/pushed_configs/mddo_network/)

### Topology (Output data)

- [topology](./topology/pushed_configs/mddo_network/topology.json)

## batfish-test-topology

[batfish-test-topology](https://github.com/corestate55/batfish-test-topology)参照
- 複数のテスト用トポロジを含んでいます
- See also: [開発用テストネットワークの分析](https://github.com/ool-mddo/playground/blob/main/demo/linkdown_simulation/doc/test_network.md)

| Snapshot | Description | Input | Queries | Output |
| --- | --- | --- | --- | --- |
| l2_sample3 | L2構成 (2switch, 2vlan) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2_sample3) | [Queries](./queries/batfish-test-topology/l2_sample3/) | [topology](./topology/batfish-test-topology/l2_sample3/) |
| l2_sample4 | L2構成 (2switch, 2vlan, 1VRF) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2_sample4) | [Queries](./queries/batfish-test-topology/l2_sample4/) | [topology](./topology/batfish-test-topology/l2_sample4/) |
| l2_sample5 | L2構成 (sample4 + 同一L2/異なるVLAN IDでの接続) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2_sample5) | [Queries](./queries/batfish-test-topology/l2_sample5/) | [topology](./topology/batfish-test-topology/l2_sample5/) |
| l3_sample1a | L3構成, (複数 OSPF area, BGP, BGP対向再現) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l3_sample1a) | [Queries](./queries/batfish-test-topology/l3_sample1a/) | [topology](./topology/batfish-test-topology/l3_sample1a/) |
| l3_sample1b | L3構成, (複数 OSPF area, BGP) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l3_sample1b) | [Queries](./queries/batfish-test-topology/l3_sample1b/) | [topology](./topology/batfish-test-topology/l3_sample1b/) |
| l2l3_demo1 | L2_sample3 + ルータ (正常系) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2l3_demo1) | [Queries](./queries/batfish-test-topology/l2l3_demo1/) | [topology](./topology/batfish-test-topology/l2l3_demo1/) |
| l2l3_demo1a | L2_sample3 + ルータ (異常系: L3 IP重複, 複数prefix混在セグメント) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2l3_demo1a) | [Queries](./queries/batfish-test-topology/l2l3_demo1a/) | [topology](./topology/batfish-test-topology/l2l3_demo1a/) |
| l2l3_demo1b | L2_sample3 + ルータ (正常系, スイッチ間ループ) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2l3_demo1b) | [Queries](./queries/batfish-test-topology/l2l3_demo1b/) | [topology](./topology/batfish-test-topology/l2l3_demo1b/) |
| l2l3_demo1c | L2_sample3 + ルータ (異常系, スイッチ間クロス(同一L2/異VLAN ID)) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2l3_demo1c) | [Queries](./queries/batfish-test-topology/l2l3_demo1c/) | [topology](./topology/batfish-test-topology/l2l3_demo1c/) |
| l2l3_demo1d | L2_sample3 + ルータ (正常系, Standalone L2 segment) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2l3_demo1d) | [Queries](./queries/batfish-test-topology/l2l3_demo1d/) | [topology](./topology/batfish-test-topology/l2l3_demo1d/) |
| l2l3_sample3 | L2_sample3 + ルータ (正常系) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2l3_sample3) | [Queries](./queries/batfish-test-topology/l2l3_sample3/) | [topology](./topology/batfish-test-topology/l2l3_sample3/) |
| l2l3_sample3err | L2_sample3 + ルータ (異常系: 複数prefix混在セグメント) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2l3_sample3err) | [Queries](./queries/batfish-test-topology/l2l3_sample3err/) | [topology](./topology/batfish-test-topology/l2l3_sample3err/) |
| l2l3_sample3err2 | L2_sample3 + ルータ (異常系: L3 IPアドレス重複) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2l3_sample3err2) | [Queries](./queries/batfish-test-topology/l2l3_sample3err2/) | [topology](./topology/batfish-test-topology/l2l3_sample3err2/) |
| l2l3_sample3err3 | L2_sample3 + ルータ (異常系: L2ループ) | [configs](https://github.com/corestate55/batfish-test-topology/tree/develop/l2l3_sample3err3) | [Queries](./queries/batfish-test-topology/l2l3_sample3err3/) | [topology](./topology/batfish-test-topology/l2l3_sample3err3/) |
