---
title: Bulk People Enrichment
excerpt: >-
  Use the Bulk People Enrichment endpoint to enrich data for up to 10 people
  with a single API call. The "Sample request body" example shows all available
  fields and is set as the default example.
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
<br />

## Credit Consumption

Using this endpoint **consumes credits** according to your account’s pricing plan.
For a summary of Apollo’s pricing, see the [Public Pricing Page ↗](https://www.apollo.io/pricing).
For detailed information about API credit usage, review the [API Enrichment](https://app.apollo.io/#/settings/credits/about) section on the _About Credits_ page (login required).

**Note:** This endpoint is **unavailable** to users on free plans.
