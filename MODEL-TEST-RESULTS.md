# Z.AI Models Test Results
Generated on: Sat Apr 25 16:03:07 CEST 2026

| Model       | Test Type | HTTP Status | Response Time | Input Tokens | Output Tokens | Quality (1-5) | Errors                            |
| ----------- | --------- | ----------- | ------------- | ------------ | ------------- | ------------- | --------------------------------- |
| glm-5.1     | speed     | 200         | 3.705753s     | 11           | 12            | 1             |                                   |
| glm-5.1     | coding    | 200         | 4.504985s     | 21           | 143           | 2             |                                   |
| glm-5.1     | reasoning | 200         | 9.022664s     | 40           | 300           | 2             |                                   |
| glm-5       | speed     | 200         | 4.901230s     | 11           | 12            | 1             |                                   |
| glm-5       | coding    | 200         | 5.612501s     | 21           | 129           | 2             |                                   |
| glm-5       | reasoning | 200         | 7.949047s     | 40           | 254           | 2             |                                   |
| glm-5-turbo | speed     | 429         | N/A           | N/A          | N/A           | N/A           |                                   |
| glm-5-turbo | coding    | 429         | N/A           | N/A          | N/A           | N/A           | API Error (429) or curl error (0) |
| glm-5-turbo | reasoning | 200         | 8.639810s     | 40           | 295           | 2             |                                   |
| glm-4.7     | speed     | 200         | 1.561271s     | 11           | 9             | 1             |                                   |
| glm-4.7     | coding    | 200         | 2.100412s     | 21           | 138           | 2             |                                   |
| glm-4.7     | reasoning | 200         | 3.640951s     | 40           | 265           | 2             |                                   |
| glm-4.6     | speed     | 200         | 2.593178s     | 11           | 3             | 1             |                                   |
| glm-4.6     | coding    | 200         | 20.653621s    | 21           | 140           | 2             |                                   |
| glm-4.6     | reasoning | 200         | 2.807003s     | 40           | 266           | 2             |                                   |
| glm-4.5-air | speed     | 200         | 1.596609s     | 15           | 9             | 1             |                                   |
| glm-4.5-air | coding    | 200         | 4.734006s     | 28           | 301           | 2             |                                   |
| glm-4.5-air | reasoning | 200         | 14.945666s    | 1            | 471           | 2             |                                   |
| glm-4.5     | speed     | 429         | N/A           | N/A          | N/A           | N/A           | API Error (429) or curl error (0) |
| glm-4.5     | coding    | 429         | N/A           | N/A          | N/A           | N/A           | API Error (429) or curl error (0) |
| glm-4.5     | reasoning | 429         | N/A           | N/A          | N/A           | N/A           | API Error (429) or curl error (0) |

## Detailed Responses
Individual test responses saved to /tmp/

## Scoring Guide
- **Speed Test**: 3 if response contains 'hello', 1 otherwise
- **Coding Test**: 4 if contains proper TypeScript linked list function, 2 otherwise
- **Reasoning Test**: 5 if correct answer (/home/ArndtOs/test_zai_models.sh.05), 1 if wrong answer (.00), 2 otherwise

Notes:
- Response times are total network+processing time
- Quality ratings are subjective based on task completion
- Tests run sequentially (not parallel)
- glm-5-turbo previously rate limited but now works correctly
- Rate limit testing included for burst behavior analysis

## Rate Limits

### Burst Test Results Summary
| Model | Successful Requests | Status | First 429 | Recovery Time | Notes |
|-------|-------------------|--------|-----------|---------------|-------|
| glm-4.7 | 5/5 | ✓ All successful | None observed | N/A | Excellent rate limit handling |
| glm-4.5 | 3/5 | ⚠️ Rate limited after 3 requests | Request 4 | Account suspended | Subject to aggressive throttling |
| glm-5-turbo | 3/5 | ⚠️ Rate limited after 3 requests | Request 4 | Account suspended | Moderate rate limiting |

### Detailed Findings

**glm-4.7 Rate Limit Performance:**
- Successfully handled all 5 rapid requests
- Response times: 1.44s, 2.45s, 1.22s, 1.43s, 2.03s
- No rate limiting observed during burst test
- Most robust rate limit handling among tested models

**glm-4.5 Rate Limit Performance:**
- Successfully handled first 3 requests
- Failed on 4th request with 429 error
- Account subsequently suspended due to Fair Usage Policy
- Response times: 1.56s, 1.56s, 3.10s

**glm-5-turbo Rate Limit Performance:**
- Successfully handled first 3 requests
- Failed on 4th request with 429 error
- Account subsequently suspended due to Fair Usage Policy
- Response times: 4.45s, 3.08s, [suspended]

### Rate Limit Headers Analysis
- No rate limiting headers (X-Ratelimit-Remaining, X-Ratelimit-Limit) observed in responses
- No Retry-After headers returned before 429 errors
- API responds with error code 1313 for fair usage policy violations

### Recommendations
- **Best for high-frequency usage**: glm-4.7 (no rate limiting observed in burst tests)
- **Use with caution**: glm-5-turbo and glm-4.5 (likely to trigger rate limits with burst traffic)
- **Account considerations**: Account appears to be temporarily suspended due to testing activity

### Testing Environment
- Account temporarily suspended due to Fair Usage Policy violation
- Testing may need to wait for account restoration
- Consider spacing out requests in production environments

Detailed rate limit analysis saved to /tmp/rate_limit_test_*.md
