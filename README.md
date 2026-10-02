# FUTURE_CS_03 – API Security Risk Analysis

## Future Interns Cyber Security Internship

**Task:** Task 3 – API Security Risk Analysis  
**Candidate:** Satyakiran Mynam  
**Target:** OWASP crAPI  
**Assessment Environment:** Kali Linux  
**Primary Tool:** cURL

---

## 1. Overview

This project contains the API Security Risk Analysis completed for the Future Interns Cyber Security Internship – Task 3.

The assessment focused on identifying API security risks involving:

- Authentication
- Authorization
- API data exposure
- Rate limiting
- Input validation
- Security-related HTTP responses

Testing was performed against OWASP crAPI, an intentionally vulnerable API security training environment.

---

## 2. Objectives

The assessment objectives were to:

1. Identify authentication and authorization weaknesses.
2. Review API responses for potential data exposure.
3. Test API rate-limiting behavior.
4. Test handling of malformed and potentially dangerous input.
5. Document security observations.
6. Provide practical remediation recommendations.

---

## 3. Testing Methodology

The following controlled tests were performed:

| Test | Result |
|---|---|
| Unauthenticated dashboard request | HTTP 401 |
| Authenticated dashboard request | HTTP 200 |
| User-ID authorization test | HTTP 404 |
| Controlled rate-limit test | No HTTP 429 observed |
| Malformed input test | HTTP 400 |

The testing was limited to the designated training environment and a dedicated test account.

---

## 4. Key Observations

### Rate Limiting

Ten controlled requests were sent to the authenticated dashboard endpoint.

No `HTTP 429 Too Many Requests` response was observed during this limited test.

This is documented as a rate-limiting observation rather than proof that the API has no rate-limiting mechanism.

### Authenticated Data Exposure

The authenticated dashboard returned several attributes belonging to the test account, including account and role information.

A cross-user data exposure vulnerability was not confirmed.

### Authentication

The dashboard endpoint returned `HTTP 401` when accessed without a valid authentication token.

With a valid token, the endpoint returned `HTTP 200`.

### Authorization

A test request to:

```text
/identity/api/v2/user/1
