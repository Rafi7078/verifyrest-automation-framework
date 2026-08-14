# VerifyREST Automation Framework
A REST API automation testing framework built with Postman, JavaScript, Newman, Node.js, and npm.
## Overview
VerifyREST automates an end-to-end booking workflow against the public Restful-Booker API.
The framework validates HTTP status codes, JSON responses, booking data, authentication, CRUD operations, dynamic variables, deletion behavior, and API response times.
## Automated Test Flow
1. API Health Check
2. Create Authentication Token
3. Create Booking
4. Get Booking by ID
5. Full Update with PUT
6. Partial Update with PATCH
7. Delete Booking
8. Verify Deleted Booking returns 404
## Current Test Results
- Requests: 8
- Test Scripts: 8
- Assertions: 42
- Failed: 0
## Tech Stack
- Postman
- JavaScript
- Newman
- Node.js
- npm
- newman-reporter-htmlextra
- Git
- GitHub Actions (planned)
## Run Tests
Install dependencies:
    npm install
Run the complete automation suite:
    npm test
Generate an HTML report:
    npm run test:report
The generated report is saved to:
    reports/VerifyREST-Test-Report.html
## Environment Setup
Copy:
    postman/environments/VerifyREST-QA.example.postman_environment.json
Create:
    postman/environments/VerifyREST-QA.local.postman_environment.json
Configure:
- baseUrl
- authUsername
- authPassword
The following values are generated dynamically during execution:
- token
- bookingId
Local environment files are excluded from Git.
## Project Structure
- `postman/collections/` - Postman collection
- `postman/environments/` - Example environment configuration
- `postman/test-data/` - Test data
- `docs/` - QA documentation
- `reports/` - Generated Newman reports
- `.github/workflows/` - CI workflow
## Security
- Local environment files are excluded from version control.
- Generated HTML reports are ignored.
- Credentials should never be committed to the repository.
## API Under Test
Restful-Booker
    https://restful-booker.herokuapp.com
## Planned Improvements
- GitHub Actions CI
- Negative API test scenarios
- Data-driven testing
- JSON schema validation
- CI report artifacts
## Author
API QA Automation portfolio project.
