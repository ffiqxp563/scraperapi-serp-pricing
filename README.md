# Best SERP API: $0.30 to $25 per 1,000 Searches, the Billing Trick Behind an 80x Spread, and How to Pick by Query Volume (Full ScraperAPI Plan Table)

A thousand Google searches through a SERP API cost somewhere between $0.30 and $25, depending on which price page you land on. Part of that spread reflects performance: latency, whether the JSON parses cleanly, whether an LLM pipeline can consume the output without a cleanup script. The rest comes from the unit printed on the price tag, because providers quote per search, per 1,000 results, per credit, or per page, and none of those mean the same thing.

ScraperAPI sits at the expensive end of that range when you buy its entry plan: $49 buys 100,000 credits and one structured Google request spends 25 of them, which comes out to about 4,000 SERP requests, or **$12.25 per 1,000**. On pure Google organic JSON, the pay-as-you-go providers beat that number by a wide margin. What ScraperAPI sells is SERP data on the same API key, proxy pool and CAPTCHA handling you already use for the rest of your scraping, and the per-request cost falls to roughly $2.30–$2.50 per 1,000 once you move up to the larger plans.

> **Quick pick**
> - Already scraping with ScraperAPI, or want SERP calls and page scraping billed on one key: **Hobby, $49/mo** for 100,000 credits (about 4,000 Google SERP requests, 20 concurrent threads), with a 7-day trial that includes 5,000 credits. 👉 [See what the Hobby plan's credits buy in Google requests](https://www.scraperapi.com/pricing?fp_ref=coupons)
> - Google organic results only, tens of thousands of keywords a day, and cost decides it: DataForSEO's standard queue at $0.60 per 1,000 searches, or Serper and Scrapingdog around $0.30. ScraperAPI does not win on that comparison, and pretending otherwise wastes your afternoon.

## Every ScraperAPI plan, with the Google request count worked out

ScraperAPI prices in credits, not searches. Every plan below is converted at 25 credits per structured Google request, the rate the company publishes for Google and Bing. Annual billing takes 10% off the monthly price on every tier except Enterprise.

| Plan | Price (monthly / annual) | Google SERP requests per month | Who it fits |  |
| --- | --- | --- | --- | --- |
| Free trial | $0 for 7 days | ~200 | Testing one keyword set before paying | [Start the trial](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Hobby | $49 / $44.10 | ~4,000 | One pipeline, small rank tracker, mixed scraping | [View Hobby](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Startup | $149 / $134.10 | ~40,000 | A few hundred keywords with pagination | [View Startup](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Business | $299 / $269.10 | ~120,000 | Country-level targeting, agency work | [View Business](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Scaling | $475 / $427.50 | ~200,000 | First tier with pay-as-you-go overflow | [View Scaling](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Professional | $975 / $877.50 | ~420,000 | High-volume tracking, 300 threads | [View Professional](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Advanced | $1,975 / $1,777.50 | ~860,000 | 500 threads, no auto-upgrade on this tier | [View Advanced](https://www.scraperapi.com/pricing?fp_ref=coupons) |
| Enterprise | Custom | 22M+ credits | Multiple teams, negotiated terms | [See Enterprise terms](https://www.scraperapi.com/pricing?fp_ref=coupons) |

The details that decide whether a plan actually works for you:

| Plan | Concurrent threads | Geotargeting | Pay-as-you-go overflow | Auto-upgrade |
| --- | --- | --- | --- | --- |
| Hobby | 20 | US & EU | No | Opt-in |
| Startup | 50 | US & EU | No | Opt-in |
| Business | 100 | Country-level | No | Opt-in |
| Scaling | 200 | Country-level | Yes | Opt-in |
| Professional | 300 | Country-level | Yes | Opt-in |
| Advanced | 500 | Country-level | Yes | Not available |
| Enterprise | 500+ | Country-level | Yes | Not available |

Two limits worth knowing before you pick a tier. **Credits do not roll over** on any plan, so an unused allowance is gone at renewal. And when you hit your concurrency cap you get a 429 response; ScraperAPI does not charge for the rejected request, but it does not queue it either, so the traffic is simply lost.

## Convert every quote to one unit before you compare

The single most useful thing you can do with a page of SERP API quotes is throw them out and rebuild them in the same unit. One Google results page holds roughly 10 organic results, so a provider advertising **$0.50 per 1,000 results** is really charging about $5.00 per 1,000 searches. Run it the other way and **$2.00 per 1,000 searches** works out to $0.20 per 1,000 results. Multiply any per-1,000-results quote by 10 to put it next to a per-1,000-searches quote.

Credits need a third conversion. Find the credit cost per request, then divide the plan price by that fraction of the allowance:

- Hobby: $49 ÷ 100,000 credits = $0.00049 per credit. A Google request spends 25 credits, so one request costs $0.01225, and 1,000 requests cost **$12.25**.
- Professional: $975 ÷ 10,500,000 = $0.0000928 per credit, or **$2.32 per 1,000** Google requests.
- Advanced: $1,975 ÷ 21,500,000 = **$2.30 per 1,000**.

That last pair explains why the entry-plan figure of $12.25 gets quoted in comparison posts and the top-tier figure of $2.30 rarely does. Both are correct, and they describe different customers.

Add-ons change the arithmetic again. JavaScript rendering adds 10 credits, premium proxies add 10, ultra-premium proxies add 30. A Google request with rendering and a premium proxy lands at 45 credits, which pushes the Hobby rate to about $22 per 1,000. The 25-credit baseline assumes a plain request with no extras.

👉 [Run your own monthly query count against ScraperAPI's credit table](https://www.scraperapi.com/pricing?fp_ref=coupons)

## Two changes that quietly doubled a lot of 2026 budgets

In September 2025 Google stopped honoring the `num=100` parameter, which many rank trackers relied on to pull 100 results in a single request. Tracking the top 100 now takes about 10 paginated requests per keyword. Providers handle depth differently and bill for it differently, so ask what a page costs before you size a plan. ScraperAPI's Google endpoint paginates through a `start` offset, and each page is a separate request that spends another 25 credits.

Mobile rankings count as their own searches. Five hundred keywords tracked on desktop and mobile is 1,000 checks per day, not 500. Tracking tools differ here too; Ahrefs, for instance, includes mobile rankings in every Rank Tracker plan, while a raw API charges for the extra device.

Put the two together for a mid-sized SEO account:

**500 keywords × 2 devices × 10 pages = 10,000 requests per day, about 300,000 per month.**

At Hobby's $12.25 per 1,000 that would cost around $3,675, except Hobby's 100,000 credits only cover 4,000 Google requests a month, roughly 133 a day. The plan cannot serve that workload at any price. Professional, at 420,000 requests for $975, covers it for roughly $696 a month. DataForSEO's standard queue at $0.60 per 1,000 would come to about $180, and Scrapingdog's volume rate near $0.29 per 1,000 to about $87.

AI answers are billed on their own line, which catches people who assume the SERP price covers everything visible on a results page. DataForSEO charges about **$1.20 per 1,000 searches** for AI Overview data against $0.60 on its standard endpoint, and Apify sells Google AI Mode as an add-on at **$2 to $5 per 1,000 searches** on paid plans. If AI Overviews are the reason you are shopping, price that line separately before you compare totals.

## Where ScraperAPI actually fits

ScraperAPI is a general web scraping API with structured search endpoints attached, not a Google-only SERP service. A standard page costs 1 credit, Amazon and Walmart cost 5, Google and Bing cost 25, LinkedIn costs 30, and the structured Google endpoint returns JSON or CSV with parameters for TLD, country code, host language, geographic location, time range and result offset. The docs list no AI Overview block and no Markdown output, so if AI Overview parsing is a hard requirement, confirm it with support before committing to an annual plan.

Latency and output quality come with caveats on both sides. A standardized third-party benchmark, run on the same query, US geolocation, desktop user agent and a single time window with 1,000 requests per API, measured ScraperAPI at **P50 4.1 seconds and P95 20.1 seconds**, and rated its JSON as basic with limited or no rich snippet support. Provider-published numbers look better: Oxylabs' own comparison table lists ScraperAPI at 100% success and a 6.5-second average. Those are different methodologies and should not be averaged into one figure.

In April 2026 ScraperAPI announced its acquisition of Traject Data, the company behind SerpWow. Both products are still sold separately, and the two sites now carry the same notice, so picking either one means buying from the same owner: a general scraping API plus a dedicated SERP product line.

Who should pay the premium:

- Teams already running ScraperAPI for page scraping who want SERP calls on the same key, the same billing balance and the same proxy and CAPTCHA handling. Consolidating two vendors into one is worth real money in engineering time.
- Workloads that mix Google results with product pages, job listings or Maps data. Splitting that across three vendors costs more in maintenance than the per-request difference.
- Buyers who want country-level targeting without building their own proxy layer. That starts at the Business tier; Hobby and Startup cover US and EU only.

Who should not:

- Anyone tracking Google organic positions at volume with no other scraping needs. DataForSEO at $0.60 per 1,000, Serper around $0.30 and Scrapingdog near $0.29 all undercut every ScraperAPI tier on that specific job.
- Anyone who needs AI Overview or AI Mode data inside the same response.
- Anyone whose monthly Google volume exceeds a few hundred thousand requests and who is price-sensitive at the margin.

👉 [Compare ScraperAPI tiers by how many Google requests each credit allowance covers](https://www.scraperapi.com/pricing?fp_ref=coupons)

## How the main alternatives compare on price and latency

Latency figures below come from one vendor-run benchmark (same query, US geolocation, desktop user agent, single UTC window, 1,000 requests per API). The publisher ranked itself first in that test, so read its own numbers with that in mind, and do not mix these with provider-published averages.

| Provider | Published price | P50 / P95 latency | Main limitation |
| --- | --- | --- | --- |
| SerpApi | $25 per 1,000 searches; $75 / 5,000; $150 / 15,000 | 2.5s / 4.6s | Highest entry price; rigid subscriptions; only successful searches billed |
| DataForSEO | $0.60 per 1,000 (standard queue), $1.20 priority, $2.00 live | 4.7s / 15.8s | Standard queue takes about 5 minutes; individuals must contact support to register |
| Bright Data | $1.50 per 1,000 pay-as-you-go; Scale $499/mo for 380,000 | 2.6s / 4.9s | Base64 images in responses; some blocks mislabeled; zone setup required |
| Oxylabs | $1.00 per 1,000 on entry, $0.90 Starter, $0.80 Advanced, priced per result type | 5.5s / 15.6s | No raw HTML; base64 images |
| Apify | $1.80–$4.50 per 1,000 pages; AI Mode and ads as add-ons | 13.7s / 30.1s | Some organic results missing or misparsed |
| HasData | $2.95 per 1,000; $59/mo covers 20,000 requests | 2.3s / 3.0s | Benchmark and pricing published by HasData itself |
| ScrapingBee | $8.20 per 1,000 | 20.9s / 41.6s | Slowest in the test; basic JSON |

Two pricing conflicts are worth flagging rather than smoothing over. Bright Data's pay-as-you-go rate is $1.50 per 1,000 in two independent sources and $3 per 1,000 in Oxylabs' own comparison table. Oxylabs' entry rate appears as $1.00 per 1,000 in the third-party benchmark and $0.50 per 1,000 in its own blog. DataForSEO's new-account credit is listed as $1 in SerpApi's write-up and as a $50 minimum deposit elsewhere. Check the vendor page before you budget.

## Questions that come up before checkout

**How many free searches do I actually get?**
SerpApi's own documentation, updated in October 2026, says 250 free searches a month; an older Oxylabs comparison lists 100. The newer, first-party figure is the safer one. ScraperAPI gives a 7-day trial with 5,000 credits, roughly 200 Google requests, and its FAQ mentions a standing free plan with 1,000 credits and 5 concurrent connections.

**Are cached searches free?**
At SerpApi, results are cached for an hour and cached searches cost nothing; adding `no_cache` forces a fresh search and a charge. ScraperAPI has no equivalent published cache policy, so every request spends credits.

**Why is AI Overview billed separately?**
Because Google loads it separately in many cases, so the provider has to make an extra request or run a second parsing pass. DataForSEO exposes it through a `load_async_ai_overview` flag at an extra $0.0006 per task, and Apify sells AI Mode as a paid add-on. Budget it as its own line item.

**Can an individual sign up for DataForSEO?**
Not through the self-serve form, according to the tested review. Companies register directly; freelancers email support, explain the use case and wait for credentials.

**Does the Google lawsuit against SerpApi affect service?**
Google filed in December 2025. A court dismissed the case in July 2026, and Google may refile. The service has kept running throughout, but anyone planning a year of dependency should read the filing first.

**Is Google's own search API going away?**
Yes, Google's official search API is closing, which is the main reason this third-party market exists and why prices have not fallen.

## Picking a plan in one pass

- Google organic results only, under 50,000 searches a month: Serper or Scrapingdog around $0.30 per 1,000. Setup is an afternoon.
- SEO pipeline that also needs backlinks, keyword and on-page data: DataForSEO at $0.60 per 1,000, accepting the roughly 5-minute standard queue.
- AI Overview data next to classic rankings, or pixel-level position tracking: SerpApi, at $25 per 1,000, with its Pixel Position API and one-hour cache.
- Already scraping pages and want SERP calls on the same key: ScraperAPI Hobby at $49, moving to Business once you need country-level targeting.

Before paying, confirm three things on the pricing page: whether failed requests are billed (SerpApi charges only for successes, ScraperAPI spends credits per request), what happens when you exceed the plan (ScraperAPI returns a 429 rather than charging overage, unless you are on Scaling or above with pay-as-you-go enabled), and how deep a single request goes before pagination starts costing extra.

👉 [Start ScraperAPI's 7-day trial with 5,000 credits and check the credit cost per request in your own dashboard](https://www.scraperapi.com/pricing?fp_ref=coupons)
