# ImmortalWrt RAX3000M RNDIS Workaround Build

This repository builds a custom ImmortalWrt firmware for **CMCC RAX3000M**
based on **hanwckf/immortalwrt-mt798x** `openwrt-21.02`, with a workaround
patch for `rndis_host.c`.

## What this build changes

It patches Linux `rndis_rx_fixup()` in `rndis_host.c`:

```c
- skb_pull(skb, msg_len - sizeof *hdr);
+ skb_pull(skb, msg_len - data_offset - 8);
