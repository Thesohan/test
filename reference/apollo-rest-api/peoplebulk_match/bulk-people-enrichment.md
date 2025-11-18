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
---
# Bulk People Enrichment

Use the Bulk People Enrichment endpoint to enrich data for up to 10 people with a single API call. To enrich data for only 1 person, use the [People Enrichment endpoint](https://docs.apollo.io/reference/people-enrichment) instead.

## Key Features

- **Batch Processing**: Enrich up to 10 people in a single request
- **Flexible Input**: Multiple ways to identify people (name, email, domain, LinkedIn URL, etc.)
- **Optional Personal Data**: Control whether to reveal personal emails and phone numbers
- **Credit Consumption**: Part of your [Apollo pricing plan](https://docs.apollo.io/docs/api-pricing)

## How It Works

Apollo relies on the information you provide to identify the correct people to enrich. **More information = better matches**. If you only provide general information (like a name without a domain or email), you might receive a `200` response but no enriched records.

The details for each person should be passed as an object within the `details[]` array.

## Personal Data Access

By default, this endpoint does **not** return personal emails or phone numbers. Use these parameters to access personal data:

- `reveal_personal_emails=true` - Retrieves personal email addresses
- `reveal_phone_number=true` - Retrieves phone numbers (requires webhook URL)

**GDPR Compliance**: Personal emails will not be revealed for people in GDPR-compliant regions.

## Rate Limits

This endpoint's [rate limit](https://docs.apollo.io/reference/rate-limits) is:
- **Per minute**: 50% of the People Enrichment endpoint's limit
- **Hourly/Daily**: 100% of the People Enrichment endpoint's limits

## Requirements

- **Apollo Plan**: Not accessible to users on free plans
- **Credits**: Consumes credits for each enriched person
- **Webhook URL**: Required when `reveal_phone_number=true`

## Request Examples

### Complete Request (Default)
This example shows all available fields you can use to identify people:

```json
{
  "details": [
    {
      "first_name": "tim",
      "last_name": "zheng", 
      "name": "tim zheng",
      "email": "tim@apollo.io",
      "hashed_email": "8d935115b9ff4489f2d1f9249503cadf",
      "organization_name": "apollo",
      "domain": "apollo.io",
      "id": "587cf802f65125cad923a266",
      "linkedin_url": "http://www.linkedin.com/in/tim-zheng-677ba010"
    }
  ]
}
```

### Minimal Request (ID Only)
If you have an Apollo ID, you can use just that:

```json
{
  "details": [
    {
      "id": "64a7ff0cc4dfae00013df1a5"
    }
  ]
}
```

## Response Structure

Successful responses include:
- `total_requested_enrichments`: Number of people you requested
- `unique_enriched_records`: Number successfully enriched
- `missing_records`: Number that couldn't be found
- `credits_consumed`: Credits used for this request
- `matches`: Array of enriched person objects with full details

## Error Handling

- **400**: Invalid request (missing details, too many people)
- **401**: Invalid API credentials
- **422**: Server processing error
- **429**: Rate limit exceeded

**Note**: Phone number data is delivered asynchronously to your webhook URL when `reveal_phone_number=true`.