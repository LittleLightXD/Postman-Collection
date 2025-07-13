ShoppersStacks API Automation Report
ShoppersStacks API Automation - Newman CLI Report
Project Overview
This project contains automated tests for the ShoppersStacks API, designed using Postman and
executed via Newman CLI.
It validates a variety of Admin and Merchant functionalities, including user registration, login, update,
and error handling.
Test Summary
- Iterations: 1
- Requests: 110
- Test Scripts: 220
- Prerequest Scripts: 141
- Assertions: 228
- Failed Assertions: 0
All tests passed successfully.
Total Run Duration: 54.7s
Data Received: 2.27MB (approx)
Average Response Time: 370ms (min: 175ms, max: 4.5s, std dev: 579ms)
Collection Name
ShoppersStacks Automation
Tools & Technologies
ShoppersStacks API Automation Report
- Postman (for API development & testing)
- Newman (for CLI execution of Postman collections)
- JavaScript (Pre-request & test scripts)
How to Run the Tests
1. Install Newman:
npm install -g newman
2. Run the collection:
newman run "ShoppersStacks Automation.json"
To generate an HTML report:
newman run "ShoppersStacks Automation.json" -r cli,html
Features Covered
- Admin registration and validations (201, 409, 404, 400, 405)
- Admin login flow with valid/invalid credentials (200, 401)
- Admin profile fetch and update with access control
- Merchant registration with embedded company/address details
- Dynamic data generation (emails, phone numbers, names)
Notes
- Uses collection variables for test flow.
- Includes negative test cases for robustness.
