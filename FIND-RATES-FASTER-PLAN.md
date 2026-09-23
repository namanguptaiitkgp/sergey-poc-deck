# Find Rates Faster — plan summary (from Naman’s Doc)
Doc: https://docs.google.com/document/d/1yAg-MdeBKlECrE8sq7rSOGfsO4YkOubV7sr1enn_8V8/edit

## Core problem
FindRates connects FFs needing ocean rates with Agents who supply them.
1) Leaky cold funnel (~7% reply); agents don’t understand FindRates / WIIFM; weak enrichment/nurture.
2) Enquiry engine is a black box: irrelevant broadcasts, no how/when to reply, no price benchmark, low trust → agents don’t quote.
Biggest barrier = trust (Cogoport/disintermediation fear) + no clear return for quoting effort.

## Goals
- Raise cold reply above ~7%
- Cold → warm → verified (engaged, not KYC)
- Raise rate-fill rate (agents who return quotes)
- Higher matching precision (less spam)
- Trust signals that replying leads to business

## Lead lifecycle
- Cold: scrape/enrich; explainer + demo + book-meeting CTA; spam controls
- Warm: human onboarding (Prashant calls); agent-side enquiry demo (not FF bot demo); bot-identity transparency / dedupe vs same-day direct quotes
- Verified: active + replied (priority), not KYC/KYB

## Onboarding requirements
Explain: FF demand base; enquiry email domain to whitelist; profile-based matching; reply in plain text; clear agent benefit narrative.

## Matching engine (target)
Score by corridor/cargo vs agent card → filter low scores → shortlist → auto email. Stop broadcasting everything to everyone. Prioritize corridor strength (e.g. India–US).

## Trust & anti-disintermediation
Human touch onboarding; address “will I get the booking if I quote?”; prevent bot re-asking on behalf of a customer the agent already quoted today.

## Indicative / benchmark pricing (Section 8)
Agents need an indicative/reference price so they know whether to pursue and can avoid long negotiation loops with no booking guarantee. Define benchmark source and how it’s shown at quote time. (This is the product theme behind tonight’s POC.)

## Point 7 / First-enquiry SLA (Section 9)
First enquiry = make-or-break trust. Dedicated human monitors. If no reply within 24h → human follow-up. Target 100% coverage.

## Success metrics (to baseline)
Cold reply rate | cold→warm | warm→verified | rate-fill | enquiry precision | first-enquiry <24h human follow-up
