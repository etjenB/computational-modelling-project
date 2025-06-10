# computational-modelling-project

1. Agent States

- S (Susceptible): hasn’t seen the anti-vax rumor yet.
- B (Believer): believes and spreads it.
- R (Recovered): exposed to fact-checks or social “refutation” and won’t believe again.
- V (Vaccinated): has proactively received accurate vaccine information (via official campaigns) and cannot transition to B.
- Z (Zealot): a hardcore anti-vax influencer who:
  - Spreads more aggressively (higher transmission probability),
  - Has very low chance of ever moving to R.

2. Dynamics

1. Initialization
   - A fraction p_V of agents start in V (pre-inoculated by public health messaging).
   - A tiny fraction p_Z are Z (the hardcore anti-vax core).
   - The rest start as S, except a seeding set in B.

2. Transitions per step
   - S → B when contacted by B or Z (with β_Z > β) for zealotss.
   - S → V if they’re targeted by a vaccination campaign (can sweep its daily “budget”).
   - B → R via:
     - Meeting a fact-checker (“teacher”),
     - Contact with R,
     - Self-recovery after hitting skepticism threshold.
   - Z → R only via extremely strong interventions (might let this be almost zero).
   - V, R never go to B or Z.

3. Interventions that can be tested
   - Pre-campaign size p_V: how many we inoculate before the rumor starts.
   - Ongoing campaign rate: daily “S→V” conversions.
   - Fact-check capacity: number of B→R conversions per day.
   - Zealot targeting: what if we focus fact-checks on high-degree Z agents?

4. Outputs
   - Peak B + Z prevalence over time.
   - Final V + R size (total “inoculated” either proactively or reactively).
   - Time to rumor extinction (B + Z falls below a threshold).

