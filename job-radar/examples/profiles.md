# Example profiles

Fictional people, for showing how to fill in `config/profile` in different markets. Resumes are shortened to "…".

## Berlin – English-speaking engineer with an EU Blue Card

```json
{
  "name": "Priya Example",
  "resume": "…",
  "roles": ["Senior Backend Engineer", "Staff Engineer"],
  "locations": ["Berlin", "Remote within Germany"],
  "home_country": "DE",
  "timezone": "Europe/Berlin",
  "languages": [
    {"lang": "English", "level": "C2", "can_write_applications": true},
    {"lang": "German", "level": "A2", "can_write_applications": false}
  ],
  "language_policy": "English-working-language roles; German A2/B1 nice-to-have is fine; skip roles requiring German B2+.",
  "work_rights": {"authorised": ["DE"], "needs_sponsorship_for": [], "notes": "EU Blue Card (Germany) – does not cover other EU countries"},
  "salary": {"amount": 80000, "currency": "EUR", "period": "year", "basis": "gross"},
  "cv_style": "DE"
}
```

## London – UK resident open to EU remote

```json
{
  "name": "Tom Example",
  "roles": ["Product Manager", "Senior Product Manager"],
  "locations": ["London", "Remote – UK", "Remote – EU timezones"],
  "home_country": "GB",
  "timezone": "Europe/London",
  "languages": [
    {"lang": "English", "level": "native", "can_write_applications": true},
    {"lang": "Spanish", "level": "B2", "can_write_applications": false}
  ],
  "work_rights": {"authorised": ["GB"], "needs_sponsorship_for": ["EU"], "notes": "British citizen"},
  "salary": {"amount": 75000, "currency": "GBP", "period": "year", "basis": "gross"},
  "cv_style": "UK"
}
```

## Bangalore – open to India and relocation to the Gulf or Singapore

```json
{
  "name": "Ananya Example",
  "roles": ["QA Lead", "SDET"],
  "locations": ["Bengaluru", "Hyderabad", "Remote – India", "Dubai (with sponsorship)", "Singapore (with sponsorship)"],
  "home_country": "IN",
  "timezone": "Asia/Kolkata",
  "languages": [
    {"lang": "English", "level": "C2", "can_write_applications": true},
    {"lang": "Hindi", "level": "native", "can_write_applications": true}
  ],
  "work_rights": {"authorised": ["IN"], "needs_sponsorship_for": ["AE", "SG"], "notes": ""},
  "salary": {"amount": 3500000, "currency": "INR", "period": "year", "basis": "gross"},
  "salary_display": "INR 35 LPA",
  "cv_style": "IN"
}
```

Note: jobs in Dubai or Singapore will show their salary in AED / SGD; Job Radar records it and says "different currency – not compared" rather than converting.

## Toronto – remote anywhere in North America

```json
{
  "name": "Sam Example",
  "roles": ["Data Analyst", "Analytics Engineer"],
  "locations": ["Toronto", "Remote – Canada", "Remote – North America"],
  "home_country": "CA",
  "timezone": "America/Toronto",
  "languages": [
    {"lang": "English", "level": "native", "can_write_applications": true},
    {"lang": "French", "level": "B1", "can_write_applications": false}
  ],
  "work_rights": {"authorised": ["CA"], "needs_sponsorship_for": ["US"], "notes": "Canadian citizen (TN-eligible for some US roles)"},
  "salary": {"amount": 95000, "currency": "CAD", "period": "year", "basis": "gross"},
  "cv_style": "CA"
}
```

## Dubai – Sunday–Thursday week

```json
{
  "name": "Omar Example",
  "roles": ["Finance Manager"],
  "locations": ["Dubai", "Abu Dhabi"],
  "home_country": "AE",
  "timezone": "Asia/Dubai",
  "week_start": "sunday",
  "languages": [
    {"lang": "Arabic", "level": "native", "can_write_applications": true},
    {"lang": "English", "level": "C1", "can_write_applications": true}
  ],
  "work_rights": {"authorised": ["AE"], "needs_sponsorship_for": [], "notes": "Employer-sponsored residence visa; a job change needs a new sponsor"},
  "salary": {"amount": 30000, "currency": "AED", "period": "month", "basis": "net"},
  "cv_style": "GCC"
}
```
