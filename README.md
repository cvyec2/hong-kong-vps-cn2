# Hong Kong VPS CN2: What $2.99/Month Actually Gets You, Which CN2 Tier You're On, and How Fast the Transfer Runs Out (Evoxt HK Plan Table)

Evoxt's Hong Kong line starts at **$2.99/month** on its Premium Network, and that price buys a 1 vCPU / 512 MB / 5 GB slice with a 1 Gbps port and a few hundred GB of monthly transfer. It's enough for a small site, an API relay or a build box. It is not enough for a control panel plus a database plus Docker on the same 5 GB disk.

The $5.99 VM-1 tier is where most buyers should land, because it's the first tier that can run Windows. Three things decide whether any Hong Kong CN2 plan is worth its price, and none of them show up on the plan card: which CN2 grade the route actually is, how fast the transfer allowance burns at port speed, and what the same box costs the month you exceed it. All three are below, with Evoxt's published HK pricing first.

> **Quick pick: VM-1 at $5.99/mo.** It's the cheapest tier with Windows available and enough RAM to run a real stack. Take the $2.99 entry plan only for a single small site, a proxy or a test box. Skip Evoxt entirely if you need dedicated cores (every plan is shared-core) or more than 5 TB/month, which is where the top HK plan caps out.
> 👉 [See Evoxt's Hong Kong CN2 plans and current pricing](https://bit.ly/EvoXt)

## Evoxt Hong Kong pricing, and the cells I left blank

| Plan | vCPU / RAM | SSD | Monthly transfer | Price | Order |
| --- | --- | --- | --- | --- | --- |
| HK entry | 1 vCPU / 512 MB | 5 GB | 250–500 GB (see note) | **$2.99/mo** | [Check the entry plan](https://bit.ly/EvoXt) |
| VM-1 | — | — | — | **$5.99/mo** | [Check VM-1 specs and price](https://bit.ly/EvoXt) |
| VM-2 | — | — | — | **$11.99/mo** | [Check VM-2 specs and price](https://bit.ly/EvoXt) |

Evoxt sells more HK tiers above VM-2, and the top one carries 5 TB of transfer. The dashes are there because two published figures for the entry tier's transfer disagree (250 GB in one, 500 GB in another), and the mid-tier spec sheets aren't published in a form I could cross-check. Deal blogs repeat both numbers, which is the reason to read the cart page yourself before paying: the allowance you see at checkout is the one you get, and it changes what the plan is good for by a factor of two.

Hong Kong sits inside Evoxt's **Premium Network** group alongside Osaka and Malaysia Premium. That grouping matters more than the brand name on the invoice, because the network tier sets both your transfer allowance and your overage rate:

| Network tier | Locations | Overage | Allowance shape |
| --- | --- | --- | --- |
| Standard | most Evoxt locations | $3/TB | up to 10 TB on the top plan, no China-optimised routing |
| Premium | Hong Kong, Osaka, Malaysia Premium | $12/TB | 250 GB on entry plans, 5 TB on the top plan |
| Premium Plus | Malaysia | $24/TB | — |

Buying "Evoxt" and buying "Evoxt Hong Kong CN2" are two different purchases with two different cost curves. The same $5.99 that gets you a Premium HK box with a small allowance would get a much larger allowance on a Standard-network location that isn't routed for China. Only pay the Premium price if mainland latency is the point.

## CN2 is three different products wearing one label

"CN2" on a product page tells you the route family, not the grade. The distinction that matters is between CN2 GT (Global Transit, shared capacity with regular traffic) and CN2 GIA (Global Internet Access, dedicated capacity). Off-peak they can look similar. During Beijing evening peak, GT starts losing packets and latency climbs while GIA holds; the transit cost difference is why real GIA plans are priced several times higher per Mbps.

Evoxt markets its Hong Kong location as "optimised routing to China via the high-quality CN2 network" and doesn't print GT or GIA next to the plan name. Most Hong Kong sellers do the same: Hostease writes "CN2 optimized," Tudcloud writes "CN2" and puts "CN2 GIA" in the page title, Server.HK writes "CN2 GIA" in its marketing copy. None of those strings is a contract.

Three questions to put to support before you pay for an annual term:

1. **Which grade is the return path, GT or GIA?** Ask specifically about return routing from mainland China to Hong Kong, not outbound.
2. **Does all three of China Telecom, Unicom and Mobile use it, or just Telecom?** A single-carrier optimisation is common and it isn't what most buyers assume.
3. **What happens when I exceed the transfer allowance, throttle or suspend?** Evoxt bills overage rather than cutting you off, which is friendlier for a site and harsher for a bill you didn't plan.

If you want the HK line without committing to a year of uncertainty, start monthly and test the route during the hours your users are actually online.
👉 [Start monthly on an Evoxt HK plan and test before committing](https://bit.ly/EvoXt)

## The port speed is not the allowance

A 1 Gbps port sounds like 1 Gbps of usable throughput. It's a ceiling, and the allowance is what you actually get:

| Port speed | Full-rate throughput | Time to burn 250 GB | Time to burn 500 GB |
| --- | --- | --- | --- |
| 1 Gbps | ~450 GB/hour | ~33 min | ~67 min |
| 100 Mbps | ~45 GB/hour | ~5.5 hours | ~11 hours |
| 20 Mbps | ~9 GB/hour | ~28 hours | ~56 hours |
| 5 Mbps | ~2.25 GB/hour | ~4.6 days | ~9 days |
| 2 Mbps | ~0.9 GB/hour | ~11.6 days | ~23 days |

A single large backup, a video upload or a misconfigured rsync job can eat a 500 GB allowance inside an hour on a gigabit port. That's fine for a website serving HTML and images; it's a trap if you plan to push files through the box.

The reverse case is just as misleading. Tudcloud's "$5 unmetered" HK plan runs at 3 Mbps, which works out to about 1.35 GB/hour, roughly 32 GB/day, or **around 970 GB a month if the line never idles**. "Unmetered" at 3 Mbps is a ~1 TB plan with a rate limit. Server.HK's cheapest tier runs at 2 Mbps, about 21 GB/day, which is why its 2 GB of RAM and $5 price point belong to a different use case than a 1 Gbps box with a 500 GB cap.

Match the shape to the job. Bursty traffic with small monthly volume wants the big port and the tight allowance. Steady streaming or a download mirror wants the rate-limited flat plan. Neither is cheaper; they're priced for different curves.

## What the overage actually costs

Premium Network overage is **$12/TB**, against $3/TB on Standard and $24/TB on Premium Plus. Compare that to the plan itself: one extra terabyte costs four times the $2.99 entry plan. It's also worth four months of the jump from $2.99 to $5.99.

That arithmetic gives you a clean rule. If you expect to run more than about 1 TB over your allowance in a typical month, change tiers instead of paying overage. If you expect one spike a year, pay the overage and stay small. Sizing for the peak month is how people end up on a $50 plan to serve 300 GB.

On billing: Evoxt's checkout carries a coupon field, and codes circulating on deal blogs go stale or get restricted to specific plans, so apply one and confirm the total changes before you pay. Confirm the renewal price for the term you're choosing at the same time. Some sellers make annual billing worse rather than better: Hostease's annual-only HK plan is $34.99/year but drops the port to 10 Mbps, while its $10 monthly plan gets 20 Mbps. Server.HK's annual pricing is a straight 20% off twelve months, which is easy to check tier by tier. Evoxt's HK plans don't publish a separate renewal rate on the plan card, so verify it in the cart before you pick a longer term.

👉 [Check VM-1's current price and allowance before you pick a tier](https://bit.ly/EvoXt)

## Who should buy something else

Hong Kong CN2 isn't one product, so a fair answer to "which is best" doesn't exist. What exists is fit:

- **Low bandwidth, lots of RAM.** Server.HK lists ten HK tiers from $5/mo (1 core, 2 GB, 30 GB, 2 Mbps) to $113/mo (14 cores, 40 GB, 20 Mbps), with annual pricing at roughly 80% of twelve monthly payments, a published 3-day money-back window and test IPs. Its page was dated 2026-06-18, about five months before this writing, so treat the promotion as unverified today. The 2 Mbps ceiling makes it a small-site and low-traffic box.
- **Rate-limited flat plans.** Tudcloud's HK CN2 line covers metered plans at $6.99 (1.5 GB / 400 GB on 20 Mbps), $13.99 (3 GB / 800 GB) and $19.99 (6 GB / 1500 GB), plus "unmetered" tiers at 3–30 Mbps from $5 to $130. Every one of them displayed **zero stock** at the time of checking, from the $5 entry to the $130 top tier. A price you can't order isn't a price.
- **Big ports with traffic caps and native IPs.** IMIDC's HK range runs $18/mo (512 MB, 500 GB, 100 Mbps) to $88.88/mo (16 GB, 3 TB, 200 Mbps), with optional residential and ISP IPs and Windows on everything except the entry plan. Useful if IP reputation is the point; the entry plan is Linux-only.
- **Cheapest 20 Mbps entry with a known name.** Hostease lists $10/mo for 1 vCPU, 1 GB, 50 GB SSD, 20 Mbps CN2 and 1 TB, with 1–2 hour deployment and Alipay/WeChat Pay support.

Evoxt's case is the $2.99 floor and the 1 Gbps port at that price. If neither matters to you, the list above has a better-fitting shape.

## Questions buyers actually ask

**Do I need an ICP licence?** No. Hong Kong sits outside mainland China's filing regime, which is why every seller in this segment advertises "no ICP." Anything you host inside the mainland does need one.

**Will it be fast in China?** Depends on the route grade and the hour, and no plan card answers that. Test after deployment between 20:00 and 23:00 Beijing time, when congestion shows up, and test to your own users' cities rather than to a benchmark server.

**Can I run Windows?** Yes, from the $5.99 tier upward, with Windows Server 2012/2016/2022 in English and Chinese builds. The $2.99 entry plan is Linux-only.

**How long until the server exists?** Provisioning is automatic and takes a couple of minutes; you get the IP and root credentials without a ticket.

**How can I pay?** Card, PayPal, Bitcoin, USDT (Tron) and Alipay are all accepted at checkout.

**Is there a refund window or a trial?** No refund period or trial is published alongside the HK plans. Get the answer in writing from support before you pay for anything longer than a month.

**What if I outgrow the plan?** You can scale up from the control panel without redeploying, which is the argument for starting at $2.99 or $5.99 and moving up once you have real traffic numbers.

**Is there a test IP?** Ask support for one. Otherwise, treat the first hours after deployment as the test: check routing to your users' networks before you put anything live.

## The decision, in four lines

- One small site, a relay or a test box, Linux only: the **$2.99** entry plan, monthly.
- A control panel plus a database, a few thousand daily visits, or Windows: **VM-1 at $5.99**.
- More than roughly 1 TB/month: check Evoxt's larger HK tiers before paying $12/TB in overage, and compare against a Standard-network location where overage is $3/TB and the allowance is bigger.
- Need dedicated cores, a published refund window or a test IP up front: Evoxt isn't the fit, and no amount of plan comparison changes that.

Two things to confirm on the cart page before you pay: the transfer allowance on the exact tier you're buying (published figures for the entry tier disagree by 2x), and the renewal price for the billing term you select. Everything else you can settle with a monthly test deployment.

👉 [See Evoxt's Hong Kong CN2 plans and current pricing](https://bit.ly/EvoXt)
