# BaseHub FinOps

This document provides a cost-management reference for teams using BaseHub across the Personal, Team, and Unlimited plans.

## Cost Summary by Plan

| Plan | Base Cost | Per-User | API Requests | Asset Storage |
|---|---|---|---|---|
| Personal | $0/mo | N/A | 75k included | 25 GB |
| Team | $15/user/mo | $15 | 500k included | 500 GB |
| Unlimited | $350/mo | Unlimited users | 5M included | 5 TB |

Annual billing saves approximately 20% on Team and Unlimited plans.

## Key Cost Drivers

### API Requests
The GraphQL API is the primary metered resource. Every SDK query, mutation, and direct fetch call counts against the monthly quota. High-traffic applications or frequent CI/CD content pulls can exhaust quotas quickly on lower-tier plans.

- Personal overage: $1 per 50,000 extra requests
- Team/Unlimited overage: $1 per 100,000 extra requests

### Asset Storage and Delivery
Media-heavy repositories should track asset storage (GB) and asset request counts separately. Asset requests (CDN hits) are metered independently from GraphQL API calls.

- Extra asset storage: $0.10/GB/month
- Extra asset requests: $1 per 1,000,000 requests

### Blocks
The Personal plan caps at 5,000 blocks. Teams migrating large content repositories should audit block counts before choosing a plan. Overage blocks cost $1 per 500 additional blocks.

## Cost Optimization Recommendations

1. **Cache GraphQL responses** at the CDN or application layer to reduce repeated API calls against the monthly quota.
2. **Use ISR / static generation** in Next.js or similar frameworks so content is fetched at build time rather than on each request.
3. **Audit block counts** before migrating to the Personal plan; 5,000 blocks can be reached quickly in content-rich repositories.
4. **Annual billing** saves 20% on Team and Unlimited — commit annually once usage patterns are stable.
5. **Monitor via the Analytics dashboard** to track API request trends and anticipate overage before month-end.
6. **Right-size the plan** — small teams with low traffic often stay within Personal limits; high-traffic production sites typically need Team or Unlimited.

## Estimating Monthly Cost (Team Plan Example)

| Usage | Cost |
|---|---|
| 3 users × $15/user | $45.00 |
| 600,000 API requests (100k overage) | $1.00 |
| 600 GB asset storage (100 GB overage) | $10.00 |
| **Total estimate** | **$56.00/month** |

Source: https://basehub.com/pricing
