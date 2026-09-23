# FindRates Manual (Wizard-of-Oz) POC Plan

**Owner:** Naman Gupta (Logicore Product Consultant / FindRates)  
**Audience:** Sergey (decision), Prashant & Ashutosh (execution), Elena/OPS (coordination), Pavel/Fedor (optional price source)  
**Duration:** 10–14 days  
**Mode:** Human simulation of planned product treatments — no new product features required  
**Status:** Ready for briefing and Sergey alignment  

---

## 1. One-page summary

FindRates connects freight forwarders (FFs) who need ocean rates with Agents who quote. Today the cold funnel roughly converts at ~7% reply. Agents experience the enquiry engine as a black box. The biggest barriers are **trust** (Cogoport / disintermediation fear) and **no clear return for quoting**.

We will **not** wait for product to ship. Instead, for 10–14 days, Sales (Prashant primary, Ashutosh co-pilot) will manually deliver the planned "Find Rates Faster" treatments to a small cohort of freshly onboarded agents:

1. Better warm onboarding (agent journey, whitelist, how to reply, WIIFM)  
2. Profile / corridor-filtered matching (no broadcast spam)  
3. Trust / anti-disintermediation provenance + human touch  
4. Indicative / benchmark pricing at enquiry time  
5. Point 7–style first-enquiry follow-up SLA (<24h, 100% coverage target)

**What we prove:** Whether these treatments raise reply rate, rate-fill, and agent trust *before* engineering builds them. If hypotheses fail, we kill or reshape features early. If they hold, we prioritize build with evidence.

**What we do not pretend:** Personal web accounts, scraping, official line integrations, and auto corridor ranges remain in progress or stuck. POC runs **in parallel** with Fedor's work; it does not depend on it.

---

## 2. Hypotheses (H1–H5)

Each hypothesis has a falsifiable prediction. Baselines marked **TBD** where we lack measured numbers — establish Day 0 from Elena/OPS tracker + last 2–4 weeks of cold outreach where available.

| ID | Hypothesis | Falsifiable prediction (10–14 days) |
|----|------------|-------------------------------------|
| **H1** | Warm onboarding that teaches *agent* journey (reply method, whitelist, WIIFM) raises first-week engagement vs cold / generic onboarding. | Treatment cohort reply-to-first-enquiry ≥ **2×** historical cold reply (~7% → target ≥14%), or ≥ cold baseline +10 pp if baseline TBD. |
| **H2** | Corridor-filtered enquiries (humans only send relevant lanes) reduce ignore / spam perception and raise quote attempt rate. | Rate-attempt rate on treatment enquiries ≥ **1.5×** unfiltered broadcast rate (TBD baseline). Agent qualitative: "relevant" ≥70% of post-call feedback. |
| **H3** | Explicit provenance ("not your existing customer you already quoted today") + human touch reduces Cogoport / disintermediation fear enough to unlock quoting. | ≥50% of treatment agents who receive provenance line quote ≥1 enquiry; exit interview "trust concern" score drops vs pre-call (simple 1–5, TBD baseline). |
| **H4** | Indicative / benchmark price at enquiry time increases willingness to quote and fill rate. | Quote completion (rate-fill) on enquiries *with* indicative price ≥ enquiries without (within cohort A/B if feasible) by ≥15 pp, or strong qualitative "helped me quote faster." |
| **H5** | 100% human follow-up within 24h of first enquiry raises first-quote conversion. | First-enquiry → first rate returned within 48h ≥ **2×** no-follow-up historical (TBD); SLA met on ≥95% of first enquiries in cohort. |

**Kill signals (any two → stop and rethink):** Reply/attempt flat vs baseline; agents say process feels "fake automation" or shady; Sales cannot sustain <24h chase; indicative prices repeatedly wrong and damage trust.

---

## 3. What we fake vs what stays real

| Element | Fake / manual (Wizard-of-Oz) | Real / unchanged |
|---------|------------------------------|------------------|
| Warm onboarding journey | Prashant/Ashutosh call + scripted walkthrough | Agent's real email / WhatsApp identity |
| Domain whitelist guidance | Explained verbally + written tip sheet | Whatever whitelist already exists in product |
| Corridor matching | Humans select & send only corridor-fit enquiries | Real FF enquiries from live funnel |
| Trust / provenance line | Human-written sentence in email / WhatsApp | Real that enquiry is not agent's known customer (ops check) |
| Indicative / benchmark price | Manual spreadsheet from Pavel/Fedor or OPS estimates | Labelled clearly as **indicative**, not bindable |
| First-enquiry <24h follow-up | Ashutosh (+ Elena handoff) phone/WhatsApp chase | Real enquiry timestamps; real chase |
| Product UI / auto matching / scraping | **Not used as "new feature"** | Existing product as-is; no fake "we built this" claims |
| KYC / verification | Out of scope for POC ("verified" = engaged, not KYC) | Existing verification if any |

**Hard rule:** Never tell agents the product automatically does X if a human did X. Frame as: *"We're piloting a concierge / priority matching lane with you — a human will help for the first enquiries."*

---

## 4. Cohort design

**Inclusion**

- Freshly onboarded agents only (first warm touch in last 0–7 days, or onboarded specifically for this POC).  
- Active ocean corridors we can supply (agree top 3–5 corridors Day 0 with Elena + Pavel/Fedor).  
- Willing to take WhatsApp/phone follow-up.  
- Suggested **n = 8–15** agents (enough for signal; small enough for 100% human coverage).

**Exclusion**

- Long-standing agents already deep in funnel (confounds "warm onboarding").  
- Agents with open Cogoport disputes or known hostile history (unless Sergey wants a trust stress-test — default: exclude).  
- Corridors with zero reliable indicative price source (park those lanes).  
- Agents who refuse human contact / email-only with no response path.

**Design options (pick one Day 0)**

1. **Preferred if volume allows:** Split cohort — Treatment (full package) vs Light control (existing Elena outreach only, no provenance/indicative/<24h Point-7 package). Same corridor pool.  
2. **If n too small:** Single treatment cohort; **before/after** within agent (first enquiry after warm call vs any pre-call behaviour) + compare to Elena's parallel non-POC outreach as informal control.  

Do **not** mix "old broadcast spam" into treatment agents during POC window.

---

## 5. Treatment package — playbook (one agent, warm call → first 3 enquiries)

### Step A — Warm onboarding call (Prashant primary; Ashutosh co-pilot as needed)

1. Confirm agent identity, corridors, response channel (email / WhatsApp).  
2. Explain **agent-facing** journey: how enquiries arrive, how to reply in **plain text**, what "good quote" looks like.  
3. Whitelist / domain tip: what to allow so mail doesn't die in spam.  
4. WIIFM: fewer irrelevant broadcasts; priority matching on *their* corridors; human help on first enquiries; clear that FindRates is not taking their customer.  
5. Set expectation: next 1–3 enquiries will include corridor fit + indicative range + human follow-up if quiet.  
6. Log call outcome in tracker (completed / no-show / reschedule).

### Step B — Corridor filter (ops + Sales)

1. Map agent corridors in tracker.  
2. When FF enquiry arrives, **only** route to treatment agents if corridor matches.  
3. If no match, do not spray — hold or route to non-POC agents per Elena's normal process.

### Step C — Enquiry send (manual "product")

For each matched enquiry, send email (and WhatsApp nudge if agreed) containing:

- Standard enquiry details (origin, destination, equipment, cargo, dates).  
- **Provenance line** (trust).  
- **Indicative / benchmark note** (from spreadsheet; labelled indicative).  
- Clear ask + reply-by hint.  
- How to reply plain text (one-liner reminder).

### Step D — Point 7 first-enquiry SLA

1. Clock starts at send timestamp.  
2. If no rate / substantive reply within **<24h**, Ashutosh (or Elena handoff) executes chase: WhatsApp then phone.  
3. Target: **100%** of first enquiries in cohort get chase or confirmation of reply before 24h elapses.  
4. Repeat light chase pattern for enquiry #2–3 if bandwidth allows; first enquiry is mandatory.

### Step E — Close loop

1. Log rate-fill, time-to-first-reply, time-to-rate.  
2. After 3 enquiries or Day 14 (whichever first), short exit questions (trust, relevance, indicative price usefulness).  
3. Naman aggregates for decision memo.

---

## 6. Roles & RACI

| Activity | Prashant | Ashutosh | Naman | Elena/OPS/Mkt | Pavel/Fedor |
|----------|----------|----------|-------|---------------|-------------|
| POC design / metrics / Sergey memo | C | I | **A/R** | C | I |
| Warm onboarding calls | **R** | C (co-pilot) | C (script) | I | — |
| Corridor matching / send selection | C | **R** | C | **R** (supply enquiries) | I |
| Provenance + indicative in send | C | **R** | A (template) | C | **C/R** (price sheet) |
| <24h first-enquiry chase | C | **R** | I | **R** (handoff / overflow) | — |
| Daily standup & tracker hygiene | R | R | **A/R** | C | I |
| Do not duplicate Elena cold spray | I | I | A | **R** (coordinate) | — |

**R** = Responsible, **A** = Accountable, **C** = Consulted, **I** = Informed.

---

## 7. Scripts & assets checklist

Prepare Day 0; store in shared drive / Slack canvas.

### 7.1 Onboarding call script outline (EN)

1. **Open:** Name, FindRates, why this call (priority / pilot matching — honest concierge framing).  
2. **Confirm:** Corridors, volumes, preferred reply channel.  
3. **Journey:** How an enquiry looks; reply in plain text (rates, validity, notes); what happens after they quote.  
4. **Whitelist:** Domain / sender tips so mail arrives.  
5. **WIIFM:** Relevant lanes only; indicative context; human follow-up on first enquiry; we do not step in as their customer.  
6. **Trust:** Explicit anti-disintermediation: enquiries are FF demand via FindRates, not hijacking their book.  
7. **Next steps:** Expect 1–3 matched enquiries this week; we'll chase if stuck; ask permission for WhatsApp.  
8. **Close:** Confirm contact; log.

### 7.2 Enquiry email template (must include)

- Subject: corridor + equipment + "FindRates matched enquiry"  
- Body: load details  
- **Provenance line (example):** "This request is from a freight forwarder on the FindRates network. It is **not** one of your existing customers that you already quoted today — we check before we send."  
- **Indicative note (example):** "Indicative market context for [POL–POD], [equip]: approx **USD X–Y** (non-binding, for orientation only — please quote your live rate)."  
- Reply instruction: plain text reply with rate / validity / remarks.  
- Sign-off: human name (Ashutosh/Prashant/Elena), not a fake bot.

### 7.3 24h chase script (WhatsApp → phone)

- WhatsApp: short nudge — enquiry ref, corridor, "need your rate today to keep this live," offer to clarify.  
- Phone: same; if no answer, voicemail + WhatsApp.  
- Never invent urgency that isn't real; never claim auto-reminder system.

### 7.4 Assets checklist

- [ ] Onboarding script (EN) + optional short tip sheet PDF  
- [ ] Enquiry email template with provenance + indicative placeholders  
- [ ] WhatsApp / phone chase snippets  
- [ ] Corridor list + agent–corridor map  
- [ ] Indicative price spreadsheet (owner: Pavel/Fedor or OPS)  
- [ ] Tracker sheet (see Appendix)  
- [ ] Exit interview 3–5 questions  
- [ ] Slack channel or thread for daily standup  

---

## 8. Daily / weekly ops cadence

**Daily (15 min standup — Naman facilitates)**

- New agents onboarded yesterday  
- Enquiries sent / matched / held  
- First-enquiry SLA: any clock approaching 24h?  
- Chases done / rates received  
- Blockers (bad prices, no FF demand on corridor, Sales bandwidth)  
- Elena coordination: avoid double-touching same agent  

**Weekly (end Week 1 & Week 2)**

- Metrics snapshot vs H1–H5  
- Qualitative themes (trust, spam, price usefulness)  
- Go / adjust / kill recommendation draft  

**Tracker discipline:** Update same day as event; Naman owns completeness; Sales owns row accuracy for their touches.

---

## 9. Metrics & instrumentation

**Log without engineering:** Google Sheet / Notion (see Appendix). Timestamps in IST (Asia/Calcutta).

| Metric | Definition | How logged |
|--------|------------|------------|
| Warm call completed | Binary + date | Sales |
| First enquiry sent (T0) | Timestamp | Ashutosh/OPS |
| Reply (any substantive) | Timestamp; binary | Sales/OPS |
| Rate filled | Timestamp; binary; rate value optional | Sales/OPS |
| Time-to-first-reply | Reply − T0 | Formula |
| Time-to-rate | Rate − T0 | Formula |
| <24h chase executed | Binary; timestamp | Ashutosh/Elena |
| SLA met | Chase or reply before 24h | Formula |
| Corridor match flag | Yes/No | OPS |
| Indicative shown | Yes/No + range used | Ashutosh |
| Provenance line included | Yes/No | Ashutosh |
| Trust score (1–5) | Pre-call + exit | Prashant/Naman |
| Qualitative notes | Free text | All |

**Success criteria (directional — finalize numbers Day 0 with Sergey once TBD baselines pulled)**

- SLA coverage ≥95% on first enquiries.  
- Treatment reply and/or rate-fill clearly above agreed baseline (H1/H2/H4/H5).  
- No major trust incident (agent accusing us of fake automation or stealing customers).  
- Sales bandwidth sustainable at n≈8–15.

**Kill criteria**

- Two or more hypotheses clearly fail with decent sample.  
- Indicative prices wrong often enough to cause complaints.  
- Team cannot keep <24h chase.  
- Framing slips into "the product does this" when it doesn't.

---

## 10. Timeline

| Phase | When | Work |
|-------|------|------|
| **Day 0 — Prep** | Before kickoff | Baselines TBD pull; cohort list; corridor + price sheet; scripts/templates; tracker; RACI confirm; Sergey 15-min align on success/kill; Elena handoff rules |
| **Week 1** | Days 1–7 | Warm calls (target fill cohort); send matched enquiries #1; 100% <24h chase; daily standup; mid-week metric check |
| **Week 2** | Days 8–14 | Enquiries #2–3; continue SLA; exit interviews; freeze new cohort adds after Day 10 unless backfill |
| **Decision** | Day 14–16 | Naman decision memo → Sergey; recommend build / reshape / kill per feature |

---

## 11. Risks & mitigations

| Risk | Mitigation |
|------|------------|
| **Lying about automation** — agent thinks product matches/prices/chases automatically | Honest "concierge / pilot" framing in every script; human names on sends; never claim shipped features |
| **Cogoport fear if manual feels shady** | Provenance line + transparent human; avoid pressure tactics; exclude hostile cases initially |
| **Sales bandwidth** (Prashant/Ashutosh overload) | Cap n=8–15; Elena overflow on chase; pause new onboards if SLA <95% |
| **Wrong indicative prices** | Label non-binding; use Pavel/Fedor ranges; widen bands; remove indicative for corridor if confidence low |
| **Duplicating Elena outreach** | Day 0 coordination; shared tracker; single owner per agent |
| **No FF demand on treatment corridors** | Pre-select corridors with history; allow week stretch; document "insufficient demand" separately from hypothesis fail |
| **Confounding product changes mid-POC** | Do not roll new auto features to cohort mid-flight; Fedor work stays parallel, not injected as treatment |

---

## 12. What NOT to build yet

Do **not** prioritize engineering for:

- Full auto profile-based matching UI  
- Automated indicative pricing in product (manual sheet is enough to learn)  
- Automated Point 7 chase bots / sequences  
- Fancy agent onboarding product flows beyond what's already in progress  
- Scraping unblocks as a POC dependency  
- KYC "verified" workflows for this experiment  
- Broad broadcast "improvements" that reintroduce spam to the cohort  

Build only after POC decision: the **minimum** that automates the treatments that moved metrics.

---

## 13. Decision memo template (for Sergey)

**Title:** FindRates Manual POC — Decision after 10–14 days  

**Period / n / corridors:** …  

**Executive verdict:** Build / Reshape / Kill (per feature)  

**Results vs H1–H5:** table with prediction vs actual; TBD baselines filled  

**Qualitative:** trust, relevance, indicative usefulness (quotes from agents)  

**Ops feasibility:** SLA %, Sales hours, Elena load  

**Recommendation by feature:**  
1. Warm onboarding —  
2. Corridor filter —  
3. Provenance / trust —  
4. Indicative pricing —  
5. <24h first-enquiry follow-up —  

**Product implications:** what Fedor/Pavel should build first; what stays manual  

**Risks observed:** …  

**Ask of Sergey:** approve next sprint priorities / stop  

---

## 14. Appendix

### A. Sample tracker columns

`agent_id | agent_name | corridors | onboard_date | warm_call_by | warm_call_status | trust_pre_1to5 | enquiry_id | corridor | sent_at_IST | provenance_yn | indicative_yn | indicative_range | matched_yn | reply_at_IST | rate_at_IST | rate_value | chase_24h_yn | chase_at_IST | sla_met_yn | notes | exit_trust_1to5 | exit_notes`

### B. Sample indicative price note format

```
Indicative market context (non-binding):
Lane: [POL] → [POD] | Equipment: [20GP/40HC/…]
Approx range: USD [low]–[high] | As of: [date IST] | Source: [internal bench / line intel / OPS]
Please quote your live sell/buy rate and validity. This range is for orientation only.
```

### C. Sample provenance line

```
This FindRates enquiry is from a network freight forwarder. Before sending, we confirmed
it is not an existing customer of yours that you already quoted today.
```

### D. Exit questions (3–5)

1. Did enquiries feel relevant to your corridors? (Y/N + why)  
2. Did the indicative range help you quote? (helped / neutral / hurt)  
3. Trust 1–5: concern that FindRates might take your customer?  
4. Was human follow-up useful or annoying?  
5. Would you keep quoting if matching stayed this way?

---

**Document control:** Naman Gupta — Manual WoZ POC plan for FindRates. Use for Sergey meeting and Prashant/Ashutosh briefing. Update baselines (TBD) on Day 0.
