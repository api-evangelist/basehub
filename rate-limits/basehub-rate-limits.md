# BaseHub Rate Limits

BaseHub enforces API request quotas at the plan level rather than per-second or per-minute burst limits. Requests are counted against a monthly allowance. Overages are billed automatically at the rates listed in the Plans document.

## Monthly API Request Quotas

| Plan | Included API Requests/Month |
|---|---|
| Personal (Free) | 75,000 |
| Team | 500,000 |
| Unlimited | 5,000,000 |

## Authentication

All GraphQL API requests to `https://api.basehub.com/graphql` must include the repository token in the `x-basehub-token` HTTP header. Requests without a valid token are rejected.

## Asset Requests

Asset delivery (images, files) is metered separately from GraphQL API calls:

| Plan | Included Asset Requests/Month |
|---|---|
| Personal (Free) | 1,000,000 |
| Team | 5,000,000 |
| Unlimited | (included, contact sales for specifics) |

## Notes

- BaseHub does not publish explicit per-second or per-minute rate-limit thresholds in public documentation. If precise burst limits are needed, consult the BaseHub help center at https://help.basehub.com or the Discord community at https://discord.gg/6Gk4qfuqHK.
- Overage API requests are billed at $1 per 50,000 (Personal) or $1 per 100,000 (Team/Unlimited).

Source: https://basehub.com/pricing, https://docs.basehub.com/api-reference
