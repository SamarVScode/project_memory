# ⚡ Wi-Fi & Network Adapter Tuning

## Context
Diagnosed a 4 Mbps (0.5 MB/s) throttle on the internal `Dell Wireless 1704 802.11b/g/n` adapter on Wi-Fi network `Airtel_arav_0600`.

## Root Causes Identified & Fixed
1. **Metered Connection Restriction:** Windows marked the network as `Cost: Fixed`. Removed via `netsh wlan set profileparameter name="Airtel_arav_0600" cost=unrestricted`.
2. **Channel Width:** Unlocked from 20MHz to `2.4G: 20/40MHz`.
3. **Power Saving Throttling:** `Minimum Power Consumption` set to `Disabled`.
4. **Packet Bursting:** `XPress (TM) Technology` set to `Enabled`.
5. **DNS:** Migrated to [[Services/Cloudflare-DNS|Cloudflare DNS (1.1.1.1)]].

## Results
* **Before:** 4.06 Mbps (0.51 MB/s)
* **After:** 24.00 Mbps (3.00 MB/s) — **6x speed boost**
* **Link Speed:** Upgraded to 108 Mbps transmit / 150 Mbps receive.
