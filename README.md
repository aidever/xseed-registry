# xseed 官方注册中心

[xseed](https://github.com/aidever/xseed) 小助手与社区节点从这里获取**签名的**节点清单、站点定义和公共 tracker 列表。

- 清单地址：<https://aidever.github.io/xseed-registry/registry.json>（签名：`registry.json.sig`）
- 签名公钥（已内置在 xseed 中）：
  - 主：`ed25519:4a8a494445a09b8e16ae8eae3002fce4c5cfd6a5b3a850590af9464a4940bc72`
  - 备用：`ed25519:650d91272c4c9acb14ba1d2545d8197b580212c03047d7845b1f6b0919e3cd13`

```sh
xseed-node registry verify registry.json ed25519:4a8a494445a09b8e16ae8eae3002fce4c5cfd6a5b3a850590af9464a4940bc72
```

## 目录

| 路径 | 内容 |
|---|---|
| `nodes/<名称>.json` | 社区节点，每个节点一个文件（`xseed-node manifest https://<域名>` 的输出） |
| `sites/<站点ID>.json` | 站点定义（站长态度 `p2p`：allow / deny / unknown） |
| `public-trackers.txt` | 补充的公共 tracker 主机 |
| `registry.json` / `.sig` | 由维护者汇总并签名的清单，**不要手工修改** |

## 提供节点

按 xseed [docs/05-发布与运维.md](https://github.com/aidever/xseed/blob/main/docs/05-发布与运维.md) §3 部署后，提交 PR 把清单条目加到 `nodes/`。维护者确认可访问后重新签发。

## 站长

希望自己的站点不参与（或明确允许）辅种，请提交 issue 或 PR 修改 `sites/<站点ID>.json` 的 `p2p` 字段。设为 `deny` 后，所有小助手收到新清单即停止在该站工作。
