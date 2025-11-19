---
title: Bulk People Enrichment
excerpt: >-
  Use the People Enrichment endpoint to enrich data for 1 person. To enrich data
  for up to 10 people with a single API call, use the <a
  href="https://docs.apollo.io/reference/bulk-people-enrichment"
  target="_blank">Bulk People Enrichment endpoint</a> instead.  <br><br>Apollo
  relies on the information you pass via the endpoint's parameters to identify
  the correct person to enrich. If you provide more information about a person,
  Apollo is more likely to find a match within its database. If you only provide
  general information, such as a name without a domain or email address, you
  might receive a 200 response, but the response will indicate that no records
  have been enriched. <br><br>By default, this endpoint does not return personal
  emails or phone numbers. Use the `reveal_personal_emails` and
  `reveal_phone_number` parameters to retrieve emails and phone numbers.
  <br><br> Using this endpoint will
  consume credits based on your account's pricing plan. To view a summary of
  Apollo's pricing, visit the [Public Pricing Page ↗](https://www.apollo.io/pricing).
  For detailed information regarding API credit usage, see the
  [API Enrichment](https://app.apollo.io/#/settings/credits/about) section on the
  *About Credits* page (login required). <br><br> **Note:** This endpoint is not
  available to users on free plans.

api:
  file: apollo-rest-api.json
  operationId: bulk-people-enrichment
hidden: false
link:
  new_tab: false
metadata:
  description: >-
    Use the Bulk People Enrichment endpoint to enrich data for up to 10 people
    with a single API call. To enrich data for only 1 person, use the <a
    href="https://docs.apollo.io/reference/people-enrichment"
    target="_blank">People Enrichment endpoint</a> instead. <br><br>Apollo
    relies on the information you pass via the endpoint's parameters to identify
    the correct people to enrich. When you provide more information, Apollo is
    more likely to find matches within its database. If you only provide general
    information, such as a name without a domain or email address, you might
    receive a `200` response, but the response will indicate that no records
    have been enriched. The details for each person should be passed as an
    object with the `details[]` array. <br><br>By default, this endpoint does
    not return personal emails or phone numbers. Use the
    `reveal_personal_emails` and `reveal_phone_number` parameters to retrieve
    emails and phone numbers. If you set either of these parameters to `true`,
    Apollo will attempt to provide emails or phone numbers for all matches.
    <br><br>{% include "_snippets/credits-and-free-plans-notice.md" %} This
    endpoint's <a href="https://docs.apollo.io/reference/rate-limits"
    target="_blank">rate limit</a> is throttled to 50% of the People Enrichment
    endpoint's per-minute rate limit, and is 100% of the hourly and daily rate
    limits for the same individual endpoint.
---
Use the Bulk People Enrichment endpoint to enrich data for up to 10 people
with a single API call. To enrich data for only 1 person, use the <a href="https://docs.apollo.io/reference/people-enrichment" target="_blank">People Enrichment endpoint</a> instead.
