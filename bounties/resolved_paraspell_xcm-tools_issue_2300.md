# Automated Bounty Resolution

- **Issue:** https://github.com/paraspell/xcm-tools/issues/2300
- **Title:** [Bug bounty] Snowbridge transfers via Dedot SDK fail with BridgeHaltedError due to raw enum return in getBridgeStatus
- **Reward:** $50 USDT (BEP-20)
- **Payout Address:** `0x1c088878957d52736337ec7a000d335a204e9b71`
- **Submitted By:** @Dungsky
- **Timestamp:** 2026-10-25T17:59:16.980Z

## Solution Summary
Fix `getBridgeStatus()` in `packages/sdk-dedot/src/DedotApi.ts` by correctly mapping the Dedot codec enum response (e.g., `{'type': 'Normal'}` or `{'type': 'Halted'}`) to the expected primitive string union (`'Normal' | 'Halted'`), preventing unintended `BridgeHaltedError` failures.

## Solution Code / Content
```
typescript
async getBridgeStatus(): Promise<TBridgeStatus> {
  const outboundOperatingMode = await this.api.query.ethereumOutboundQueue.operatingMode();
  const statusType = (outboundOperatingMode as any)?.type ?? outboundOperatingMode;
  return statusType as TBridgeStatus;
}

```
