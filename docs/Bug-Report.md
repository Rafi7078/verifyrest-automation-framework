# VerifyREST Bug Report
## Purpose
This document defines the defect reporting format used for issues discovered during VerifyREST API testing.
## Bug Report Template
### Bug ID
`BUG-API-XXX`
### Title
Short and clear description of the defect.
### Environment
- API: Restful-Booker
- Base URL: `https://restful-booker.herokuapp.com`
- Test Tool: Postman / Newman
- Execution: Local / CI
- Operating System: Windows
### Severity
Choose one:
- Critical
- High
- Medium
- Low
### Priority
Choose one:
- P1
- P2
- P3
- P4
### Preconditions
Describe any required authentication, booking data, environment variables, or previous API operations.
### Steps to Reproduce
1. Configure the required environment.
2. Send the relevant API request.
3. Provide required request data.
4. Observe the response.
### Expected Result
Describe the expected API behavior.
### Actual Result
Describe the actual API behavior.
### Evidence
Include when applicable:
- Request method
- Endpoint
- Request body
- HTTP status code
- Response body
- Newman output
- HTML report
- Screenshot
### Reproducibility
Example:
`5/5 attempts`
### Status
Choose one:
- Open
- In Progress
- Fixed
- Retest
- Closed
- Cannot Reproduce
### Notes
Add any additional investigation details.
---
## Current Defect Status
No confirmed product defects are currently documented in this portfolio test cycle.
During development, intermittent behavior was observed while manually testing the shared public Restful-Booker environment, including stale or reused booking IDs and state-dependent responses.
These observations were treated as public test-environment limitations rather than confirmed application defects.
The automated suite creates a fresh booking during each complete run to reduce dependency on existing shared data.
## Defect Handling Process
When an automated test fails:
1. Review the failing assertion.
2. Check the HTTP status and response body.
3. Confirm environment variables.
4. Reproduce the request manually in Postman.
5. Determine whether the issue belongs to the API, test script, test data, or public environment.
6. Create a bug report only when the unexpected behavior is reproducible and supported by evidence.
