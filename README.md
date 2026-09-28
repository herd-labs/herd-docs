# Herd Documentation

Public documentation for Herd's agent tools, supported chains, and Herd Action Language (HAL).

## Local development

Install the [Mintlify CLI](https://www.npmjs.com/package/mint), then run:

```bash
mint dev
```

Open [http://localhost:3000](http://localhost:3000).

## Source of truth

Keep tool and chain claims aligned with the main `herd` repository:

- Public MCP tools: `packages/mcp-tools/src/toolkits/external.ts`
- Registered EVM chains: `packages/chains/src/registry/evm.ts`
- Fully indexed chains: `packages/chains/src/registry/clickhouse.ts`
- Chain capabilities: `packages/chains/src/registry/capabilities.ts`
- HAL reference: `packages/mcp-tools/src/resources/hal.ts`

Changes merged to the default branch deploy through the Mintlify GitHub integration.
