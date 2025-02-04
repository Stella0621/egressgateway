<!--

# E2E Cases for EgressGateway

- all case about check the `eip` will include tcp, udp and web socket

| Case ID  | Title                                                                                                                                           | Priority  | Smoke  | Status | Other |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------|--------|-------|
| G00001   | Creating an EgressGateway fails when using invalid `Ippools`                                                                                    | p2        | false  |        |       |
| G00002   | Creation of EgressGateway fails when `NodeSelector` is empty                                                                                    | p2        | false  |        |       |
| G00003   | Creation of EgressGateway fails when `DefaultEIP` is not in scope of `Ippools`                                                                  | p2        | false  |        |       |
| G00004   | Creation of EgressGateway fails when the number of `Ippools.IPv4` and `Ippools.IPv6` does not match                                             | p2        | false  |        |       |
| G00005   | When `DefaultEIP` is empty, when creating EgressGateway, this field will randomly assign an IP from `Ippools`                                   | p2        | false  |        |       |
| G00006   | When `Ippools` is a single IP, the EgressGateway is successfully created and the `EgressGatewayStatus` check is passed                          | p2        | false  |        |       |
| G00007   | When `Ippools` is an IP range in `a-b` format, the EgressGateway is successfully created and the `EgressGatewayStatus` check passes             | p2        | false  |        |       |
| G00008   | When `Ippools` is in IP cidr format, EgressGateway is successfully created and `EgressGatewayStatus` check is passed                            | p2        | false  |        |       |
| G00009   | Updating EgressGateway fails when adding invalid IP addresses to `Ippools`                                                                      | p2        | false  |        |       |
| G00010   | Updating EgressGateway fails when removing IP addresses in use from `Ippools`                                                                   | p2        | false  |        |       |
| G00011   | Updating EgressGateway fails when adding different number of IPs to `Ippools.IPv4` and `Ippools.IPv6`                                           | p2        | false  |        |       |
| G00012   | Updating EgressGateway succeed when adding same number of IPs to `Ippools.IPv4` and `Ippools.IPv6`                                              | p2        | false  |        |       |
| G00013   | Add legal IP address to `Ippools`, update EgressGateway successfully                                                                            | p2        | false  |        |       |
| G00014   | Edit the `NodeSelector` to match another `node`, `Status.NodeList` is updated to the newly matched node, using the `policy` of this `EgressGateway`, `Status.Node` is updated to the newly matched `node`, the `pod`'s egress ip is eip<br>Edit the `NodeSelector` to not match any `node`, `Status.NodeList` is empty, using the `policy` of this `EgressGateway`, `Status.Node` is empty, accessing external IP from the pod will error<br>Edit the `NodeSelector` to match one `node`, `Status.NodeList` is the matched `node`, using the `policy` of this `EgressGateway`, `Status.Node` is updated to the newly matched `node`, the `pod`'s egress ip is eip                                                               | p2        | false  |        |       |
| G00015   | Deleting an `EgressGateway` fails when there is a `Policy` (both at the namespace level and at the cluster level) that is using the `EgressGateway`   | p2        | false  |        |       |
| G00016   | When `EgressGateway` is not used by `Policy`, the `EgressGateway` is deleted successfully                                                             | p2        | false  |        |       |
| G00017   | When creating an `EgressCluster` or `EgressClusterPolicy` without specifying `spec.egressGatewayName`, the tenant or cluster default gateway can be automatically configured and created successfully                                                             | p2        | false  |        |       |
| G00018  | When `Ippools.IPv4` and `Ippools.IPv6` are empty, creating `EgressGateway` succeeds                                                           | p2        | false  |        |       |
| G00019  | When `Ippools.IPv4` and `Ippools.IPv6` are empty, creating `EgressCluster` or `EgressClusterPolicy` without specifying `spec.egressIP.useNodeIP` will fail to create the policy. When `spec.egressIP.useNodeIP` is set to true, the policy will be created successfully                                                           | p2        | false  |        |       |
-->

# EgressGateway E2E 用例
- 用例中，所有有关 `eip` 校验的内容，都包含了 tcp，udp 和 web socket

| 用例编号   | 标题                                                                                                     | 优先级 | 冒烟    | 状态 | 其他 |
|--------|--------------------------------------------------------------------------------------------------------|-----|-------|----|----|
| G00001 | 使用不合法的 `Ippools` 时，创建 EgressGateway 会失败                                                                | p2  | false |    |    |
| G00002 | 当 `NodeSelector` 为空时，创建 EgressGateway 会失败                                                              | p2  | false |    |    |
| G00003 | 当 `DefaultEIP` 不在 `Ippools` 范围内，创建 EgressGateway 会失败                                                   | p2  | false |    |    |
| G00004 | 当 `Ippools.IPv4` 和 `Ippools.IPv6` 的数量不一致时，创建 EgressGateway 会失败                                         | p2  | false |    |    |
| G00005 | 当 `DefaultEIP` 为空，创建 EgressGateway 时，此字段会从 `Ippools` 中随机分配一个 IP                                        | p2  | false |    |    |
| G00006 | 当 `Ippools` 为单个 IP 时，创建 EgressGateway 成功，`EgressGatewayStatus` 检查通过                                    | p2  | false |    |    |
| G00007 | 当 `Ippools` 是 `a-b` 格式的 IP 范围时，创建 EgressGateway 成功，`EgressGatewayStatus` 检查通过                          | p2  | false |    |    |
| G00008 | 当 `Ippools` 是 IP cidr 格式时，创建 EgressGateway 成功，`EgressGatewayStatus` 检查通过                               | p2  | false |    |    |
| G00009 | 向 `Ippools` 中添加 不合法的 IP 地址时，更新 EgressGateway 会失败                                                       | p2  | false |    |    |
| G00010 | 从 `Ippools` 中删除 正在被使用的 IP 地址时，更新 EgressGateway 会失败                                                     | p2  | false |    |    |
| G00011 | 向 `Ippools.IPv4` 和 `Ippools.IPv6` 添加不同数量的 IP 时，更新 EgressGateway 会失败                                    | p2  | false |    |    |
| G00012 | 向 `Ippools.IPv4` 和 `Ippools.IPv6` 添加相同数量的 IP 时，更新 EgressGateway 会成功                                    | p2  | false |    |    |
| G00013 | 向 `Ippools` 中添加合法的 IP 地址，更新 EgressGateway 成功                                                           | p2  | false |    |    |
| G00014 | 编辑 `NodeSelector` 使其匹配另一个节点，`Status.NodeList` 更新为新匹配的节点，使用该 EgressGateway 的 policy `Status.Node` 更新为新匹配的节点, `pod` 的出口 `ip` 为 `eip`<br>编辑 `NodeSelector` 使其不匹配任何节点，`Status.NodeList` 为空，用该 EgressGateway 的 policy `Status.Node` 为空, `pod` 使用访问外部 IP 会报错<br>编辑 `NodeSelector` 使其匹配一个节点，`Status.NodeList` 为所匹配的节点，使用该 EgressGateway 的 policy `Status.Node` 更新为新匹配的节点，`pod` 的出口 `ip` 为 `eip`                           | p2  | false |      |     |
| G00017 | 创建 `EgressCluster` 或者 `EgressClusterPolicy` 时使用未指定 `spec.egressGatewayName` 时，可以使用自动设置租户或者集群默认网关，并创建成功 | p2  | false |    |    |
| G00018 | 当 `Ippools.IPv4` 和 `Ippools.IPv6` 为空时，创建 EgressGateway 成功 | p2  | false |    |    |
| G00019 | 当 `Ippools.IPv4` 和 `Ippools.IPv6` 为空时，创建 `EgressCluster` 或者 `EgressClusterPolicy`，未指定 `spec.egressIP.useNodeIP` 时，policy 创建失败，`spec.egressIP.useNodeIP` 为 true 时，policy 创建成功 | p2  | false |    |    |