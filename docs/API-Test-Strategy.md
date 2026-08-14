# VerifyREST API Test Strategy
## 1. Objective
The purpose of this strategy is to define the overall API testing approach used in the VerifyREST Automation Framework.
The framework focuses on functional REST API validation using Postman, JavaScript, Newman, and Node.js.
## 2. Testing Approach
The automation follows an end-to-end sequential workflow.
The sequence is important because later requests depend on data created by earlier requests.
Execution flow:
1. Health Check
2. Authentication
3. Create Booking
4. Get Booking
5. Full Update
6. Partial Update
7. Delete Booking
8. Verify Deletion
## 3. API Validation Strategy
The framework validates:
- HTTP status codes
- Response body content
- JSON response format
- Required response fields
- Data accuracy
- Data persistence
- Update behavior
- Delete behavior
- Response time
## 4. Dynamic Data Handling
The framework uses Postman environment variables for dynamic values.
Dynamic variables:
- `token`
- `bookingId`
The booking ID returned by the Create Booking request is automatically stored and reused by subsequent requests.
This prevents hard-coded booking IDs and makes each execution independent.
## 5. Authentication Strategy
The authentication endpoint generates a token and validates successful authentication.
Protected booking operations use configured authentication credentials.
Authentication values are stored in a local environment file that is excluded from Git.
## 6. Assertion Strategy
JavaScript assertions are written in Postman post-response scripts.
Assertions validate:
- Expected HTTP codes
- JSON responses
- Returned field values
- Updated field values
- Unchanged fields after PATCH
- Successful deletion
- 404 response after deletion
- Response time thresholds
Current automated suite contains:
    Requests: 8
    Test Scripts: 8
    Assertions: 42
## 7. CRUD Coverage
The framework covers the core booking lifecycle:
- Create - POST
- Read - GET
- Full Update - PUT
- Partial Update - PATCH
- Delete - DELETE
An additional GET request verifies that the deleted resource is no longer available.
## 8. Environment Strategy
Two environment concepts are used:
### Local Environment
Used during development and test execution.
Contains configured values such as:
- baseUrl
- authUsername
- authPassword
The local environment file is excluded from Git.
### Example Environment
A safe example environment is committed to the repository.
It documents required variables without exposing local credentials.
## 9. Execution Strategy
The test suite can be executed through:
### Postman Collection Runner
Used for interactive development and debugging.
### Newman CLI
Used for command-line automation.
### npm
Primary local execution command:
    npm test
HTML reporting command:
    npm run test:report
## 10. Reporting Strategy
Console results are generated through Newman.
HTML reports are generated using:
    newman-reporter-htmlextra
Generated reports are stored inside the `reports` directory and excluded from Git.
## 11. Response Time Validation
Selected requests include a response-time assertion.
Current threshold:
    Less than 2000 ms
This validation is intended as a basic responsiveness check and is not a substitute for dedicated performance testing.
## 12. Test Independence
A new booking is created during each complete test execution.
The generated booking ID is stored dynamically.
This reduces dependency on existing public test records and minimizes issues caused by stale booking IDs.
## 13. Public API Limitations
Restful-Booker is a shared public testing API.
Possible external issues include:
- API downtime
- Slow responses
- Shared test data
- Booking ID reuse
- Data resets
- Intermittent public environment behavior
Failures caused by these conditions should be distinguished from automation defects.
## 14. Security Strategy
The framework follows basic repository security practices:
- Local environment files are ignored.
- Generated reports are ignored.
- Credentials are not committed.
- Example configuration uses placeholder credentials.
## 15. Future Strategy Improvements
Future enhancements may include:
- Negative testing
- Invalid authentication scenarios
- Missing-field validation
- Boundary-value testing
- Data-driven testing
- JSON schema validation
- GitHub Actions execution
- Automated CI report artifacts
