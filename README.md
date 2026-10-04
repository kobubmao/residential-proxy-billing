# residential proxy: how per-IP vs per-GB billing actually works, and how to pick a plan that matches your workload

Most residential proxy pricing pages give you the same thing: a long column of tiers, a "from $X/GB" headline, and no answer to the only question that matters. How much will this cost for the job I'm actually running?

Getting that wrong is expensive in a quiet way. A per-GB plan is the wrong shape for a task that pushes 40 GB through three addresses, and a per-IP plan is wasted money on a task that touches 50,000 pages with 200 KB of text each. Below is how the two billing models behave, a real price list to reason with, and the checks worth doing before you top up an account.

## What you're buying, underneath the marketing

A residential proxy routes your request through an IP address assigned by a consumer ISP to a real household connection. Servers evaluating traffic look at network reputation before almost anything else: is this ASN a hosting provider's range, or a residential one? Datacenter IPs fail that first check, which is why they get blocked before your headers, TLS fingerprint, or request timing ever get evaluated.

The practical consequences:

- **Block rates drop.** Failed requests are retries, and retries are time and bandwidth you paid for.
- **Geo results become accurate.** Search results, product prices, ad placements, and shipping options all change by location. A country-level exit isn't enough for local SEO or ad verification, where you usually need city or ZIP.
- **Session identity survives.** A stable IP across a multi-step flow (cart, pagination, login) behaves like a person. An IP that hops cities mid-session behaves like exactly what it is.

9Proxy reports a pool of 20M+ residential IPs across 90+ countries with targeting down to country, state, city, ISP, and ZIP level, and supports HTTP/HTTPS plus SOCKS5. Those pool and uptime figures are vendor-reported, so treat them as claims to test rather than audited numbers. You can inspect the current package tiers yourself here: 👉 [see 9Proxy's live residential proxy packages](https://bit.ly/9-Proxy).

## Per-GB vs per-IP: two different cost curves

Both models appear on almost every provider's page, and they fail in opposite directions.

**Per-GB** charges for transferred data. It fits high-rotation work where each request is small: SERP checks, price lookups, API polling, light scraping, geo-verification. The catch is that failures still consume bandwidth. A CAPTCHA page or a block page is data you pay for, and browser-rendered scraping pulls images, fonts, and tracking pixels you never wanted.

**Per-IP** charges a fixed price per address with unlimited traffic during that address's lifetime. It fits work where a small number of IPs carry heavy load: long scraping jobs, bulk file pulls, sustained automation where you can't predict volume. It's a bad fit for anything that needs thousands of distinct exits.

Two smaller models exist and are usually not what you want unless your workload is unusual: per-request billing (fine for scraping APIs, painful at volume) and monthly subscriptions (predictable, but unused quota just expires). 9Proxy takes a different route from the subscription norm and sells balance-based packages instead, which is worth unpacking because it changes how you plan spend.

## The current 9Proxy price list, start to finish

9Proxy sells three product lines: IP-based packages, GB-based packages, and bundles that combine both. GB-based pricing has stayed flat; IP-based and bundle pricing changed on 1 June 2026, so older articles quoting $0.015/IP are out of date.

### IP-based residential packages

Fixed IP count, unlimited bandwidth per activated IP, balance that doesn't expire until you spend it.

| Package | What you get | Price (USD) | Effective rate | Buy |
| --- | --- | --- | --- | --- |
| 100 IPs | 100 residential IPs, unlimited traffic | $24 | $0.24 per IP | [get the 100 IP package](https://bit.ly/9-Proxy) |
| 500 IPs | 500 residential IPs | $72 | $0.144 per IP | [get the 500 IP package](https://bit.ly/9-Proxy) |
| 1,000 IPs (+500 bonus) | 1,500 residential IPs | $126 | $0.084 per IP | [get the 1,000 IP package](https://bit.ly/9-Proxy) |
| 2,500 IPs | 2,500 residential IPs | $210 | $0.084 per IP | [get the 2,500 IP package](https://bit.ly/9-Proxy) |
| 5,000 IPs | 5,000 residential IPs | $360 | $0.072 per IP | [get the 5,000 IP package](https://bit.ly/9-Proxy) |
| 15,000 IPs | 15,000 residential IPs | $720 | $0.048 per IP | [get the 15,000 IP package](https://bit.ly/9-Proxy) |
| 25,000 IPs | 25,000 residential IPs | $863 | $0.035 per IP | [get the 25,000 IP package](https://bit.ly/9-Proxy) |
| 50,000 IPs | 50,000 residential IPs | $1,438 | $0.029 per IP | [get the 50,000 IP package](https://bit.ly/9-Proxy) |
| 100,000 IPs (Business) | High-volume IP allocation | $2,300 | $0.023 per IP | [get the 100,000 IP Business package](https://bit.ly/9-Proxy) |
| 200,000 IPs (Business) | High-volume IP allocation | $4,140 | $0.021 per IP | [get the 200,000 IP Business package](https://bit.ly/9-Proxy) |
| 500,000 IPs (Business) | High-volume IP allocation | $8,625 | $0.018 per IP | [get the 500,000 IP Business package](https://bit.ly/9-Proxy) |

Per-IP IPs stay online for a few hours up to roughly 24 hours, which is normal for real household connections. Unused IP balance doesn't expire, and any IP you've already forwarded can be reused free from the Today List within 24 hours as long as it's still online. That reuse rule quietly cuts the effective cost of iterative jobs.

### GB-based residential packages

Traffic-based, rotating or sticky sessions, 180-day validity except on Enterprise tiers where the balance never expires.

| Package | Traffic | Price (USD) | Effective rate | Validity | Buy |
| --- | --- | --- | --- | --- | --- |
| 5 GB | 5 GB | $15 | $3.00 per GB | 180 days | [get the 5 GB package](https://bit.ly/9-Proxy) |
| 50 GB (+5 GB bonus) | 55 GB | $105 | $2.10 per GB | 180 days | [get the 50 GB package](https://bit.ly/9-Proxy) |
| 100 GB | 100 GB | $150 | $1.50 per GB | 180 days | [get the 100 GB package](https://bit.ly/9-Proxy) |
| 200 GB | 200 GB | $200 | $1.00 per GB | 180 days | [get the 200 GB package](https://bit.ly/9-Proxy) |
| 1,000 GB | 1,000 GB | $800 | $0.80 per GB | 180 days | [get the 1,000 GB package](https://bit.ly/9-Proxy) |
| 2,000 GB | 2,000 GB | $1,500 | $0.75 per GB | 180 days | [get the 2,000 GB package](https://bit.ly/9-Proxy) |
| 3,000 GB (Enterprise) | 3,000 GB | $2,160 | $0.72 per GB | No expiry | [get the 3,000 GB Enterprise package](https://bit.ly/9-Proxy) |
| 6,000 GB (Enterprise) | 6,000 GB | $4,200 | $0.70 per GB | No expiry | [get the 6,000 GB Enterprise package](https://bit.ly/9-Proxy) |
| 10,000 GB (Enterprise) | 10,000 GB | $6,800 | $0.68 per GB | No expiry | [get the 10,000 GB Enterprise package](https://bit.ly/9-Proxy) |

Enterprise also unlocks team collaboration and centralized traffic management, which matters if more than one person is spending from the same balance.

### Bundle packages

Both resources in one purchase, priced below buying them separately.

| Package | What you get | Price (USD) | Buy |
| --- | --- | --- | --- |
| Starter bundle | 100 IPs + 5 GB | $30 | [get the Starter bundle](https://bit.ly/9-Proxy) |
| Popular bundle | 1,500 IPs + 50 GB | $180 | [get the Popular bundle](https://bit.ly/9-Proxy) |
| Pro bundle | 5,000 IPs + 500 GB | $720 | [get the Pro bundle](https://bit.ly/9-Proxy) |

Bundles suit mixed workloads where part of the pipeline needs identity stability and part needs wide rotation. You can compare all three lines on the same page: 👉 [view all 9Proxy packages](https://bit.ly/9-Proxy).

## Working out your own number first

Run the math before you pick a tier. Say you're scraping 10,000 product pages averaging 500 KB each. That's roughly 5 GB of raw HTML. At 9Proxy's entry GB tier, that's one $15 package. So far, so cheap.

Now add what actually happens in production. If you render pages in a browser, JavaScript, fonts, tracking pixels, and images are pulled too, and real consumption often lands 3 to 5 times above your text-size estimate. Retries after a block add more, and every CAPTCHA page you hit is billable data. Your 5 GB job becomes 15 to 25 GB, which pushes you into the $105 or $150 tier.

The same job on the IP-based side looks different. If 200 residential IPs can carry the whole crawl with unlimited bandwidth, you're at roughly $29 worth of IP balance, and bandwidth stops being a variable you have to forecast. That's the scenario where per-IP wins, and it's the scenario most pricing guides skip past.

The reverse is also true: if your workflow needs a different exit for each of 30,000 requests with tiny payloads, buying IPs is nonsense. Use per-GB.

## Session behaviour decides more than the price tag

The single biggest configuration mistake is buying the right plan and using the wrong session mode.

**Rotating mode** hands each request a fresh IP. Use it for scraping, rank checks, and monitoring, where continuity doesn't matter and spread matters a lot.

**Sticky mode** holds one IP for a set window. 9Proxy controls this through the proxy username rather than the dashboard: a string like `subaccount-country-us-sst-15` keeps a US IP for 15 minutes, and adding `ssid` gives you several parallel sticky IPs from one configuration. Targeting parameters sit in the same string, so `country-us-city-newyork-st-ohio-isp-as22773...` narrows the pool to a specific ISP.

Two practical warnings. Over-filtering hurts you: stacking state, city, and ISP filters shrinks the available pool and slows response times, so target by country alone unless you genuinely need narrower. And on IP-based proxies, keep concurrency around three threads per address; pushing more degrades throughput rather than improving it.

If your target needs an identity that persists for weeks, residential rotating proxies are the wrong tool entirely. Their natural ceiling is hours to about a day, and an IP that changes under a logged-in session is one of the classic re-verification triggers.

## What you install, and what you don't

Setup differs by product line, which catches people out after purchase.

- **IP-based proxies** work through local port forwarding, so they normally require the 9Proxy desktop app (Windows, macOS, Linux). Proxy2Web removes that requirement for browser-based retrieval and testing.
- **GB-based proxies** don't need any app. Credentials and targeting go straight into your tool from the dashboard, with username/password auth or IP whitelisting.
- **For pipelines**, the 9Proxy API covers session control and usage stats programmatically.
- **For anti-detect browsers and automation stacks**, native SOCKS5 support means you paste an endpoint into Dolphin Anty, AdsPower, Multilogin, or a Python script without protocol conversion. HTTP works for rank trackers that accept proxy fields.

Test one endpoint before you scale anything. Confirm the exit IP matches the country you asked for and that nothing leaks.

## Where residential is the right call, and where it isn't

Residential proxies earn their cost on: large-scale scraping of defended sites, regional price monitoring, SERP and rank tracking from real local exits, ad verification and cloaking checks, geo-QA of pricing and shipping flows, and multi-account operations where the platform's terms allow it.

They're the wrong spend when you're polling a friendly API at high frequency, when speed is the only metric that matters, or when you need one identity held for months. Datacenter proxies and static ISP proxies exist for those jobs, and paying residential rates for them is just a premium on a problem you don't have.

One thing worth stating plainly: proxy type doesn't change what you're allowed to do. Rate limits, robots directives where they apply, and each site's terms still govern the job.

## Payment, trials, and refunds before you top up

A few details from 9Proxy's own help documentation that affect the buying decision:

- **Payment methods:** credit cards, bank cards, Alipay, Apple Pay, Google Pay, and crypto (USDT, BTC, ETH, LTC, DOGE and others). PayPal is not supported.
- **Crypto bonus:** paying in crypto adds an extra 5% IP bonus.
- **Wallet and auto top-up:** you can preload the 9Proxy wallet and pay instantly from balance, with automatic refills when it runs low.
- **Trial:** 9Proxy runs a limited trial for new accounts, subject to availability. You need to tell support whether you want to test the IP-based or GB-based model, and the allocation isn't guaranteed.
- **Refunds:** the service is sold as a digital product with no standard return window. Refunds are reviewed case by case for payment or proxy failures caused by system errors.
- **Shared accounts:** team members can use one account, but all consumption draws from the same balance, and sub-accounts are the cleaner path for controlling access.

## What independent reviewers say

Aggregator listings put 9Proxy in the value tier of the residential market. One directory shows an editorial score around 4.78 with a user score closer to 4.33, and a June 2026 comparison piece places it among the cheapest per-GB options with the caveat that budget providers can trail premium networks on tier-3 targets. Not everything is glowing: a user report in mid-2026 described roughly a week of service disruption, and the aggregator noted it couldn't confirm whether that was a technical fault.

That's a fair summary of the risk profile for any budget provider. Verify the network against your own target sites before committing to a large balance.

## Quick answers

**Do unused IPs expire?** No. The balance only decreases when you activate IPs.

**Does GB traffic expire?** 180 days on standard GB packages, no expiry on Enterprise tiers.

**How long does one residential IP stay online?** A few hours to about 24 hours, varying naturally per IP.

**Can I reuse an IP I already paid for?** Yes, free from the Today List within 24 hours if it's still online.

**Do I need to install software?** Only for the IP-based product. GB-based works entirely from the dashboard.

**What's the cheapest way to test the network?** The 5 GB package at $15, or 100 IPs at $24 if your workload is bandwidth-heavy rather than rotation-heavy.

**Which model should a typical scraper pick?** If you can't forecast bandwidth, buy IPs. If you need maximum rotation with small payloads, buy GB.

If you've worked out roughly how many GB or how many addresses your job needs, the rest is just picking the matching tier and testing it against a real target: 👉 [create a 9Proxy account and check the current packages](https://bit.ly/9-Proxy).
