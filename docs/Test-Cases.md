# VerifyREST API Test Cases
## Test Suite Summary
| Item | Value |
|---|---|
| API Under Test | Restful-Booker |
| Base URL | https://restful-booker.herokuapp.com |
| Automated Requests | 8 |
| Automated Assertions | 42 |
| Execution Tools | Postman, Newman, npm |
## Automated Test Cases
### TC-API-001 - API Health Check
- **Method:** GET
- **Endpoint:** `{{baseUrl}}/ping`
- **Purpose:** Verify that the API is available.
- **Expected:** HTTP 201, body contains `Created`, response time below 2000 ms.
- **Assertions:** 3
### TC-API-002 - Create Authentication Token
- **Method:** POST
- **Endpoint:** `{{baseUrl}}/auth`
- **Purpose:** Verify authentication with valid credentials.
- **Expected:** HTTP 200, JSON response, non-empty token returned.
- **Dynamic Action:** Save token to environment variable `token`.
- **Assertions:** 3
### TC-API-003 - Create Booking
- **Method:** POST
- **Endpoint:** `{{baseUrl}}/booking`
- **Purpose:** Verify successful booking creation.
- **Expected:** HTTP 200, numeric booking ID, correct booking data.
- **Test Data:** Rafi / Automation / 750 / Breakfast.
- **Dynamic Action:** Save generated ID to `bookingId`.
- **Assertions:** 5
### TC-API-004 - Get Booking by ID
- **Method:** GET
- **Endpoint:** `{{baseUrl}}/booking/{{bookingId}}`
- **Purpose:** Verify retrieval of the newly created booking.
- **Expected:** HTTP 200, JSON response, all created booking fields match.
- **Response Time:** Below 2000 ms.
- **Assertions:** 9
### TC-API-005 - Full Booking Update
- **Method:** PUT
- **Endpoint:** `{{baseUrl}}/booking/{{bookingId}}`
- **Authentication:** Basic Auth
- **Purpose:** Verify complete booking update.
- **Expected:** HTTP 200 and all supplied fields updated.
- **Updated Data:** RafiUpdated / AutomationQA / 1200 / Dinner.
- **Assertions:** 8
### TC-API-006 - Partial Booking Update
- **Method:** PATCH
- **Endpoint:** `{{baseUrl}}/booking/{{bookingId}}`
- **Authentication:** Basic Auth
- **Purpose:** Verify partial update without changing unrelated fields.
- **Expected:** First name becomes `RafiPatch`, additional needs becomes `Lunch`.
- **Unchanged:** Last name, price, deposit status, and booking dates.
- **Assertions:** 8
### TC-API-007 - Delete Booking
- **Method:** DELETE
- **Endpoint:** `{{baseUrl}}/booking/{{bookingId}}`
- **Authentication:** Basic Auth
- **Purpose:** Verify successful booking deletion.
- **Expected:** HTTP 201, response contains `Created`.
- **Response Time:** Below 2000 ms.
- **Assertions:** 3
### TC-API-008 - Verify Deleted Booking
- **Method:** GET
- **Endpoint:** `{{baseUrl}}/booking/{{bookingId}}`
- **Purpose:** Verify that the deleted booking is no longer available.
- **Expected:** HTTP 404, response contains `Not Found`.
- **Response Time:** Below 2000 ms.
- **Assertions:** 3
## Assertion Summary
| Test Case | Assertions |
|---|---:|
| TC-API-001 | 3 |
| TC-API-002 | 3 |
| TC-API-003 | 5 |
| TC-API-004 | 9 |
| TC-API-005 | 8 |
| TC-API-006 | 8 |
| TC-API-007 | 3 |
| TC-API-008 | 3 |
| **Total** | **42** |
## Latest Execution Result
    Requests: 8
    Test Scripts: 8
    Assertions: 42
    Failed: 0
The test cases execute sequentially because the CRUD operations depend on the booking ID generated during booking creation.
