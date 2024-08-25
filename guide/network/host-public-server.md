# 自建公共服务器

用户可以使用自己的公网节点自建用于无公网 IP 组网的公共服务器，方便其他无公网 IP 的用户组网。

只需要不带任何参数启动 EasyTier，该节点就可作为公共服务器使用（不需要 root 权限）：

```
easytier-core
```

另外，默认情况下， EasyTier 的每个节点都允许为其他虚拟网提供转发服务，即使该节点已经指定了 网络名 (`--network-name`) 和 网络密钥 (`--network-secret`)、并已加入一个虚拟网。

若需改变此行为，可通过 `--relay-network-whitelist` 参数限定可被转发的网络名白名单（空格分割的通配符列表，如 ` "ab* abc" `）。当该参数的列表为空时，就不会为所有其他网络提供转发服务。

EasyTier 可以做到不转发其他虚拟网的网络包，而是只帮助他们建立 P2P 链接，只需将白名单置空，并设置仅转发 RPC 流量即可。参考命令为：

```
easytier-core --relay-network-whitelist --relay-all-peer-rpc
```