# Work rights and postings

Goal: never put a job in the tracker that the candidate cannot legally take, and never hide a sponsorship question. This is a matching aid, not legal advice; when unsure, keep the job and flag it.

## Profile shape

```jsonc
"work_rights": {
  "authorised": ["DE"],            // ISO alpha-2 codes or region tags
  "needs_sponsorship_for": ["GB", "US"],
  "notes": "German Blue Card holder"
}
```

Region tags: `EU` (27 EU members), `EEA` (EU + IS, LI, NO), `EU+CH` (EEA + Switzerland), `GCC` (AE, SA, QA, KW, BH, OM), `ANZ` (AU + NZ only when the candidate says they hold rights in both).

Do not assume that a right in one country covers another. A national work permit or EU Blue Card from one EU country does **not** by itself give the right to work in another EU country - only EU/EEA/Swiss citizenship (tag `EU`/`EEA`) does. If the profile says "EU" but the notes suggest a single-country permit, treat it as that one country and flag it in the report.

## Reading postings

| Posting says | Meaning | Action |
|---|---|---|
| "EU work authorisation required", "must have the right to work in the UK", "no visa sponsorship", "local candidates only", "must be authorised to work in the US without sponsorship" | Must already be authorised | Keep only if the job's country/region is in `authorised` |
| "Visa sponsorship available", "relocation and visa support", "we sponsor Skilled Worker visas", "H-1B sponsorship" | Sponsorship offered | Keep if the country is in `authorised` or `needs_sponsorship_for`; note "Sponsorship offered" |
| Nothing about authorisation | Unknown | Keep; `work_auth: "Not stated"`; lower score a little if the country isn't in `authorised` |
| "Remote - [country/region] only", "must be based in", "within CET ±2 hours" | Location-restricted remote | Keep only if the candidate lives there / can work from there; timezone limits checked against `timezone` |
| "Contractor only", "B2B", "freelance / self-employed" | Contract type, not authorisation | Keep if the candidate's profile allows contract work; note it in `gaps` |
| Security clearance or citizenship required | Restricted | Skip unless the profile says they hold it |

## Wording for the job's `work_auth` field

- "Covered – <country/region> rights"
- "Sponsorship offered"
- "Sponsorship needed – posting silent"
- "Not stated"
- "Remote limited to <countries/timezones>"
