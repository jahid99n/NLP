# MIS5308 Week 3 PBL: PulseWear Vantage Influencer Strategy (working draft)

> **How to use this draft:** these are worked findings, numbers and structure. Rewrite the prose in your own words before you submit. The brief says the submission must be your own work, so check your subject's rules on AI assistance and acknowledge it if they require that. Submission format: Arial/Calibri 11 pt, 1.5 line spacing, page numbers, captioned figures, APA 7.

All numbers below come from `week3_analysis.py` (outputs are in `results/` and `figures/`).

---

## 1. Advanced network analysis

### 1.1 Network mapping and metrics

**Method.** The 11 interactions were modelled as a multi-layer network (Kivelä et al., 2014). There is one layer each for Instagram, Twitter/X and LinkedIn, plus an inter-layer set of two *Cross* ties. Edge weights are the interaction intensity (1 to 4). Centrality was calculated on the aggregated, undirected, weighted graph:

- degree (activity)
- betweenness (brokerage; Freeman, 1977). For the weighted version, distance = 1/weight.
- eigenvector (connection to well-connected others; Bonacich, 1987)
- PageRank on the directed graph (who *receives* amplification)

Communities were detected with Louvain modularity optimisation (Blondel et al., 2008; seed = 42).

**Table 1. Key node metrics** (full table: `results/node_metrics.csv`)

| Influencer | Platform | Degree | Betweenness | Eigenvector | PageRank | Burt constraint | Articulation point |
|---|---|---|---|---|---|---|---|
| FitSara | Instagram | 3 | **0.72** | 0.18 | 0.03 | **0.33** | Yes |
| TechNova | Instagram | 2 | **0.50** | 0.23 | 0.02 | 0.50 | Yes |
| GadgetGuyX | Twitter | 3 | 0.39 | **0.61** | 0.14 | 0.61 | Yes |
| ProCoach | LinkedIn | 3 | 0.39 | 0.10 | **0.15** | 0.61 | Yes |
| RunSmart | Instagram | 2 | 0.22 | 0.08 | 0.04 | 0.50 | Yes |
| DataDev | Twitter | 2 | 0.00 | **0.62** | 0.14 | 1.01 | No |
| PulseGuru | Twitter | 2 | 0.00 | 0.37 | 0.14 | 1.01 | No |
| HealthInsider | LinkedIn | 2 | 0.00 | 0.05 | 0.15 | 1.01 | No |
| DrWearable | LinkedIn | 2 | 0.00 | 0.07 | 0.15 | 1.01 | No |
| ZenLife | Instagram | 1 | 0.00 | 0.01 | 0.05 | 1.00 | No |

**Communities.** Louvain found three communities, and each one lines up exactly with a platform:

- C1 = Instagram: TechNova, FitSara, RunSmart, ZenLife
- C2 = LinkedIn: ProCoach, DrWearable, HealthInsider
- C3 = Twitter/X: GadgetGuyX, DataDev, PulseGuru

Modularity is **Q = 0.57**. Anything above about 0.3 counts as strong community structure (Newman, 2006).

**Insight.** This confirms the CMO's "fragmentation" diagnosis. The audiences are platform silos, and only **two weak (weight = 1) ties** join them: TechNova–GadgetGuyX (Collaboration) and FitSara–ProCoach (Reshare). The Twitter and LinkedIn triangles are dense but closed (layer density = 1.0), so messages loop inside them. The Instagram layer is a chain, which makes it the least cohesive, with the highest reach but fragile paths. See Figures 1 and 2.

### 1.2 Cross-platform influence and bridges

- **FitSara is the primary bridge.** FitSara has the highest betweenness (0.72) and the lowest Burt constraint (0.33), so this influencer spans the most structural holes (Burt, 1992). FitSara is the only node that links Instagram to LinkedIn.
- **TechNova is the Instagram→Twitter gateway.** Betweenness is 0.50, and the participation coefficient is the highest in the network (0.38; Guimerà & Amaral, 2005), so TechNova's ties are spread across the most communities.
- **GadgetGuyX and ProCoach are the "landing" bridges** on the receiving side. Both have betweenness 0.39. ProCoach has the highest PageRank (0.15), which means amplification flows *into* this account.
- **Cross-platform amplification potential** means reaching the other clusters. It therefore depends on the bridge *pairs* (TechNova→GadgetGuyX, FitSara→ProCoach), not on one influencer alone. Removing any of the five articulation points splits the network.
- **Caution (non-obvious finding):** DataDev has the *highest* eigenvector score (0.62) but zero betweenness. The score is inflated by the strong Retweet tie inside a closed triangle, so this is echo-chamber centrality, not wider influence.

### 1.3 Influencer suitability and decision matrix

**Brand identity assumption.** No guideline document was supplied. PulseWear is assumed to be innovative, health and performance focused, credible and data-driven, premium and positive. Each tone and content type was scored against these five values on a 1–5 scale. For example, *Humorous / Tech* = 2 (humour carries brand-safety risk for a health product), and *Motivational / Fitness* = 5.

**ROI proxy.** Estimated conversions = Followers × CTR × Conversion rate (this assumes CR is click→purchase). Cost per conversion = Cost per post ÷ estimated conversions (Figure 4). FitSara video gives **$4.4 per conversion**, against **$41.7** for GadgetGuyX short tweets, a 9.5× gap.

**Table 2. Decision matrix** (each criterion min–max normalised to 0–1, then weighted)

| Influencer | Reach 15% | Engagement 15% | Network influence 20% | Bridging 15% | Brand fit 20% | Cost efficiency 15% | **Score /100** | Tier |
|---|---|---|---|---|---|---|---|---|
| FitSara | .55 | .65 | .18 | .87 | 1.00 | 1.00 | **70** | Priority |
| TechNova | 1.00 | .29 | .18 | .85 | .67 | .85 | **62** | Priority |
| RunSmart | .36 | .53 | .12 | .15 | 1.00 | .92 | **52** | Priority |
| HealthInsider | .33 | .23 | .52 | .00 | 1.00 | .00* | **39** | Secondary |
| ProCoach | .09 | .15 | .57 | .66 | .67 | .00* | **38** | Secondary |
| ZenLife | .08 | 1.00 | .12 | .00 | .33 | .71 | 36 | Reserve |
| DataDev | .00 | .29 | .95 | .15 | .33 | .00* | 32 | – |
| GadgetGuyX | .18 | .00 | .94 | .64 | .00 | .00 | 31 | – |
| PulseGuru | .03 | .18 | .73 | .00 | .67 | .00* | 31 | – |
| DrWearable | .27 | .03 | .52 | .00 | .67 | .07 | 29 | – |

\*No campaign data yet, so these influencers are conservatively scored as the least efficient. This is a known bias against untested influencers, and it is one reason the secondary tier gets a test budget.

Network influence = mean(eigenvector, PageRank). Bridging = mean(weighted betweenness, participation coefficient).

**Recommendations**

- **Priority 1: FitSara.** The top bridge, with the best cost per conversion ($4.4 on video) and a motivational fitness persona that fits a smartwatch closely.
- **Priority 2: TechNova.** Has the largest reach (520k) and is the only Instagram→Twitter gateway. Use video only: TechNova's carousel posts cost 1.7× more per conversion.
- **Priority 3: RunSmart.** Sporty running content is an exact use case for the product, and cost is $7.4 per conversion. The role here is to deepen the Instagram cluster rather than to bridge it.
- **Secondary: ProCoach.** Is the LinkedIn-side bridge and the landing point for FitSara's reshares. Pairing the two creates the Instagram→LinkedIn path. Untested, so start with a pilot.
- **Secondary: HealthInsider.** Has the largest LinkedIn reach (210k) and a Health-Tech credibility fit for the B2B and corporate-wellness angle. Untested.
- **Not recommended now: GadgetGuyX.** Despite being a structural bridge, GadgetGuyX has the worst efficiency ($41.7), the lowest engagement (2.9%) and a humorous tone. Keep as an optional *paid-amplification* node for TechNova's content only.

**Sensitivity check:** three alternative weightings were tested: brand fit 30% with network influence 10%; bridging 25% with reach and engagement 10% each; and reach 25%. In all three, the top three (FitSara, TechNova, RunSmart) stay in the same order, so the priority tier is robust. The secondary slots shift slightly: GadgetGuyX enters the top five when bridging is weighted most heavily.

---

## 2. Multi-layer A/B testing strategy

### 2.1 Hypotheses

- **H1 (primary):** Bridge influencers (FitSara, TechNova, ProCoach) produce a higher conversion rate and ROAS than single-cluster influencers (RunSmart, HealthInsider, ZenLife) for PulseWear Vantage.
  - H0: CR(bridge) = CR(single).
- **H2 (secondary, format):** Short-form video produces a higher click→purchase CR than carousel or long-form posts. The existing data supports this: video averages 1.8% CR against 0.8–0.9% for carousel and long-form.
- **H3 (secondary, amplification):** Content cross-posted along a bridge pair (for example FitSara→ProCoach) reaches more *unique* users and new-customer conversions than single-platform posting.
- **H4 (secondary, interaction):** The format effect differs by influencer type (bridge × format interaction).

### 2.2 Experimental design (parallel and nested)

- **Layer 1 (between-influencer, parallel):** bridge vs single-cluster, 3 influencers per arm, matched on platform where possible.
- **Layer 2 (nested within each influencer):** each influencer posts every format in a randomised order:
  - T2a (bridge arm): short video vs carousel
  - T2b (single-cluster arm): short video vs long-form educational
- **Layer 3 (audience level):** each post carries a unique UTM tag and discount code. Viewers are randomised by the tracking link between **landing-page variant A and B**, which keeps the influencer effect separate from the page.

The unit of analysis is the click (session), clustered within post and within influencer. Analyse with a mixed-effects logistic regression:

`purchase ~ influencer_type * format + (1 | influencer) + (1 | post)`

### 2.3 Sample size, significance and test length

Two-proportion formula (Kohavi et al., 2020):

n per arm = [z₁₋α/₂ · √(2p̄(1−p̄)) + z₁₋β · √(p₁(1−p₁) + p₂(1−p₂))]² ÷ (p₂ − p₁)²

The baseline is p₁ = 1.48% (the pooled click→purchase rate across current campaigns), with α = 0.05 (two-sided) and power = 0.80.

**Table 3. Clicks needed per arm** (`results/ab_sample_size.csv`)

| Minimum detectable lift | Independent clicks | With clustering (ICC = 0.01, ~2,000 clicks per post; DEFF ≈ 21) |
|---|---|---|
| +20% | 28,651 | ≈ 601,000 |
| **+30% (recommended)** | **13,302** | ≈ 279,000 |
| +50% | 5,197 | ≈ 109,000 |

**What this means:**

- A single post by FitSara or TechNova generates roughly 19–20k clicks, so the *click-level* requirement is met within the first posting cycle.
- The binding constraint is the **small number of influencers**. With 3 influencers per arm, even a strong effect is hard to prove at the influencer level. Increase the number of posts per influencer (at least 8 over 4 weeks), use the mixed model above, and report confidence intervals, not just p-values.
- **Test length:** 4 weeks, which covers full weekly cycles and dampens novelty effects, plus a 1-week hold-out to measure lagged purchases.
- **Significance rules:** α = 0.05, power = 0.80, and a Holm–Bonferroni correction across H1–H4.
- **No peeking:** there are no early stops unless a pre-registered sequential boundary (O'Brien–Fleming) is crossed.

### 2.4 Control and randomisation

- **Randomisation protocol:**
  - Use stratified block randomisation. The strata are platform and follower band (<150k and ≥150k).
  - Within each stratum, influencers are assigned to posting slots, and formats are ordered using a seeded random number generator. An analyst who is not choosing influencers runs it, and the seed and assignment are logged before launch (pre-registration).
  - Viewer-level landing-page variants use hash-based bucketing of an anonymous session ID.
- **Control variables (held constant):**
  - posting window (weekdays 18:00–20:00 in the audience's local time)
  - the same hashtag set (#PulseWearVantage and #TrackYourPulse)
  - the same 10% discount offer (the code differs only for tracking)
  - the same product claims, CTA wording and landing page (except for the audience-level test)
  - no paid boosting during the test
  - a creative brief with a fixed video length (under 45 seconds)
- **Covariates to adjust for:** follower count, historical engagement rate, and audience overlap between influencers. Because of overlap, a viewer can be exposed to both arms, so use unique codes and first-touch attribution.
- **Contamination and interference:** bridge influencers are, by definition, linked to other nodes (FitSara→ProCoach). To avoid spillover, schedule linked pairs so they post in *different* weeks, and exclude cross-exposed users by cookie or code when estimating H1.

---

## 3. Strategic integration

### 3.1 Dashboard mock-up

Figure 5 combines four elements:

- KPI tiles: conversions per arm, baseline CR, modularity and test window
- the annotated network with bridge nodes marked
- the suitability ranking
- the A/B test tracker: status, CTR→CR funnel and ROAS per arm, updated daily from UTM and code data

**Live KPIs to add after launch:**

- CR and cost per acquisition by arm
- incremental unique reach per bridge
- share of new customers
- sentiment of comments
- frequency per user (a signal of audience fatigue)

### 3.2 Risk–benefit analysis

| Risk | Likelihood / impact | Mitigation built into the design |
|---|---|---|
| **Audience fatigue:** the Instagram cluster is a chain, so the same followers see FitSara, TechNova and RunSmart repeatedly | High / Medium | Frequency cap; staggered posting weeks; track frequency and CR decay on the dashboard; rotate formats |
| **Algorithm changes** (for example, reach throttled on Reels or on link posts) | Medium / High | Spread across three platforms; measure the conversion *rate per click*, which is less exposed to reach than raw reach; keep a hold-out control |
| **Influencer scandal** or off-brand behaviour | Low / High | Morals clause and a brand-safety review of the past 12 months of posts; no single influencer takes more than 35% of the budget; secondary tier on standby |
| **Over-reliance on a few bridges:** the two cross-ties are weak (weight 1), and removing FitSara disconnects LinkedIn | Medium / High | Develop more bridges (brief HealthInsider and DataDev on cross-platform collabs); monitor bridge strength each month |
| **Small-sample false positives** (only 6 influencers) | High / Medium | Mixed model, pre-registration, Holm correction, report effect sizes and intervals |
| **Legal and ethical exposure:** undisclosed ads, or tracking without consent | Medium / High | #ad and paid-partnership labels (ACCC and AANA guidance; FTC for the US); consent-based cookies; analytics on aggregated, anonymised data under the Privacy Act 1988 and GDPR |
| **Data limitations:** a partially anonymised, 10-node sample; CTR and CR definitions assumed; brand-fit scores are judgement calls | High / Medium | State the assumptions openly; run a sensitivity analysis; validate with the pilot before scaling budget |

### 3.3 Short strategic rationale (write this part in your own words; max 2 pages)

Points to make:

1. The conversion problem is **structural**. Engagement circulates inside three platform silos (Q = 0.57), joined by only two weak ties.
2. Spending should therefore move from *reach* toward **bridge activation**: FitSara, TechNova and their landing partners ProCoach and GadgetGuyX.
3. Efficiency data points the same way. Instagram video from brand-aligned fitness creators converts 5–9× more cheaply than Twitter or LinkedIn text formats.
4. The test design turns this from an assumption into evidence within about 5 weeks, with controls that separate the influencer effect from format, timing and offer.
5. The risks are mostly about concentration: fatigue, dependence on bridges, and scandals. The design diversifies and monitors each of these explicitly.

---

## Figures (all in `figures/`)

- Figure 1: Annotated multi-layer network, with communities, bridges and betweenness (`fig1_multilayer_network.png`)
- Figure 2: Platform layers as small multiples (`fig2_layers.png`)
- Figure 3: Degree, betweenness and eigenvector centrality (`fig3_centrality.png`)
- Figure 4: Estimated cost per conversion by influencer × format (`fig4_cost_per_conversion.png`)
- Figure 5: Dashboard mock-up (`fig5_dashboard_mockup.png`)

## References (APA 7)

Blondel, V. D., Guillaume, J.-L., Lambiotte, R., & Lefebvre, E. (2008). Fast unfolding of communities in large networks. *Journal of Statistical Mechanics: Theory and Experiment, 2008*(10), P10008. https://doi.org/10.1088/1742-5468/2008/10/P10008

Bonacich, P. (1987). Power and centrality: A family of measures. *American Journal of Sociology, 92*(5), 1170–1182. https://doi.org/10.1086/228631

Burt, R. S. (1992). *Structural holes: The social structure of competition*. Harvard University Press.

Freeman, L. C. (1977). A set of measures of centrality based on betweenness. *Sociometry, 40*(1), 35–41. https://doi.org/10.2307/3033543

Guimerà, R., & Amaral, L. A. N. (2005). Functional cartography of complex metabolic networks. *Nature, 433*(7028), 895–900. https://doi.org/10.1038/nature03288

Kivelä, M., Arenas, A., Barthelemy, M., Gleeson, J. P., Moreno, Y., & Porter, M. A. (2014). Multilayer networks. *Journal of Complex Networks, 2*(3), 203–271. https://doi.org/10.1093/comnet/cnu016

Kohavi, R., Tang, D., & Xu, Y. (2020). *Trustworthy online controlled experiments: A practical guide to A/B testing*. Cambridge University Press. https://doi.org/10.1017/9781108653985

Newman, M. E. J. (2006). Modularity and community structure in networks. *Proceedings of the National Academy of Sciences, 103*(23), 8577–8582. https://doi.org/10.1073/pnas.0601602103
