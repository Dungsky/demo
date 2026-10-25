# Automated Bounty Resolution

- **Issue:** https://github.com/paraspell/xcm-tools/issues/2294
- **Title:** [Bug bounty] Hydration dry-run bypasses minting due to unhandled currencyId shape in transform
- **Reward:** $50 USDT (BEP-20)
- **Payout Address:** `0x1c088878957d52736337ec7a000d335a204e9b71`
- **Submitted By:** @Dungsky
- **Timestamp:** 2026-10-25T17:59:14.671Z

## Solution Summary
Fix currencyId transformation logic in XcmTransformer by ensuring correct recursive inspection and shape handling for multi-key asset structures on Tokens-pallet parachains like Hydration.

## Solution Code / Content
```
export class XcmTransformer {
  static transform(obj: any): any {
    if (!obj || typeof obj !== 'object') return obj;
    if (Array.isArray(obj)) return obj.map(item => XcmTransformer.transform(item));
    
    const transformed: Record<string, any> = {};
    for (const key of Object.keys(obj)) {
      let value = obj[key];
      if (key === 'currency_id' || key === 'currencyId') {
        if (typeof value === 'string' && /^[0-9]+$/.test(value)) {
          value = Number(value);
        } else if (value && typeof value === 'object') {
          value = XcmTransformer.transform(value);
        }
      } else {
        value = XcmTransformer.transform(value);
      }
      transformed[key] = value;
    }
    return transformed;
  }
}
```
