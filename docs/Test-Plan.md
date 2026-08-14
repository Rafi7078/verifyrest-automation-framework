# VerifyREST API Automation Test Plan
## 1. Purpose
This test plan defines the testing approach for the VerifyREST Automation Framework.
The objective is to validate the functional behavior of the Restful-Booker API through an automated end-to-end booking workflow using Postman, JavaScript, Newman, and Node.js.
## 2. Scope
The following API operations are included:
- API health validation
- Authentication token generation
- Booking creation
- Booking retrieval by ID
- Full booking update using PUT
- Partial booking update using PATCH
- Booking deletion
- Verification that a deleted booking returns 404
## 3. In-Scope Testing
The automated suite validates:
- HTTP status codes
- JSON response format
- Required response fields
- Authentication response
- Dynamic booking ID generation
- Booking data accuracy
- PUT update behavior
- PATCH update behavior
- Preservation of unchanged fields
- Delete operation
- 404 response after deletion
- Response time below defined thresholds
## 4. Out of Scope
The current version does not cover:
- Performance or load testing
- Security penetration testing
- Database validation
- UI testing
- Cross-browser testing
- Large-scale concurrency testing
- Complete negative-test coverage
These may be included in future versions.
## 5. Test Environment
API Under Test:
    https://restful-booker.herokuapp.com
Tools:
- Postman
- JavaScript
- Newman
- Node.js
- npm
- newman-reporter-htmlextra
Execution environments:
- Postman Collection Runner
- Newman CLI
- npm scripts
## 6. Test Data
The framework creates booking data dynamically during execution.
Dynamic environment variables include:
- token
- bookingId
Local authentication values are stored in a Git-ignored local Postman environment file.
## 7. Test Execution Flow
1. Check API availability.
2. Generate an authentication token.
3. Create a booking.
4. Save the generated booking ID.
5. Retrieve and validate the booking.
6. Perform a full update using PUT.
7. Perform a partial update using PATCH.
8. Delete the booking.
9. Verify that the deleted booking returns HTTP 404.
## 8. Entry Criteria
Testing can begin when:
- The Restful-Booker API is reachable.
- Node.js and npm are installed.
- Project dependencies are installed.
- The Postman collection is available.
- Required local environment variables are configured.
## 9. Exit Criteria
The automated test cycle is considered successful when:
- All 8 requests execute.
- All expected test scripts execute.
- All 42 assertions pass.
- No unexpected test failures occur.
- The delete-verification request returns the expected 404 response.
## 10. Expected Result
Successful execution should produce:
    Requests: 8
    Test Scripts: 8
    Assertions: 42
    Failed: 0
## 11. Reporting
Test execution results are available through:
- Newman CLI output
- Postman Collection Runner
- HTML report generated with newman-reporter-htmlextra
Generated HTML reports are stored inside:
    reports/
Generated reports are excluded from Git.
## 12. Risks and Limitations
The Restful-Booker API is a public testing service.
Possible risks include:
- Temporary API downtime
- Slow responses
- Public test data resets
- Booking IDs being reused
- Intermittent behavior caused by shared public usage
These conditions may cause failures unrelated to the automation framework.
## 13. Future Improvements
Planned improvements include:
- Negative API test scenarios
- Data-driven testing
- JSON schema validation
- GitHub Actions CI execution
- CI report artifacts
- Additional validation scenarios
