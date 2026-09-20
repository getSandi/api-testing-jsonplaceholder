# API Testing - JSONPlaceholder

## 📌 Project Overview

This project is an **API Testing and Automation** project using **Postman** and **Newman**.

The purpose of this project is to test the functionality and response of the JSONPlaceholder REST API using manual API testing in Postman and automated execution using Newman.

The test cases cover basic **CRUD operations**:

* GET
* POST
* PUT
* PATCH
* DELETE

## 🌐 API Under Test

**Base URL:**

`https://jsonplaceholder.typicode.com`

JSONPlaceholder is a free fake REST API for testing and prototyping.

## 🛠️ Tools & Technologies

| Tool / Technology | Purpose                                           |
| ----------------- | ------------------------------------------------- |
| Postman           | API testing and test script creation              |
| Newman            | Running Postman collections from the command line |
| Newman HTML Extra | Generating HTML test reports                      |
| JavaScript        | Writing API assertions                            |
| REST API          | API architecture under test                       |
| JSON              | Request and response data format                  |
| Git & GitHub      | Version control and portfolio documentation       |


## 🧪 Test Coverage

The collection contains 8 automated API test cases:

| Test Case  | Method | Endpoint    | Description         |
| ---------- | ------ | ----------- | ------------------- |
| TC-API-001 | GET    | `/posts`    | Get all posts       |
| TC-API-002 | GET    | `/posts/1`  | Get post by ID      |
| TC-API-003 | DELETE | `/posts/1`  | Delete post         |
| TC-API-004 | DELETE | `/posts/10` | Delete post         |
| TC-API-005 | POST   | `/posts`    | Create new post     |
| TC-API-006 | POST   | `/posts`    | Create another post |
| TC-API-007 | PUT    | `/posts/1`  | Update post         |
| TC-API-008 | PATCH  | `/posts/1`  | Update post title   |

## 🔍 Automated Assertions

The project uses JavaScript test scripts in Postman to validate API responses.

### Status Code Validation

```javascript
pm.test("Status code harus 200", function () {
    pm.response.to.have.status(200);
});
```

### JSON Response Validation

```javascript
pm.test("Response harus berupa JSON", function () {
    pm.response.to.be.json;
});
```

### Response Data Validation

```javascript
pm.test("Response tidak boleh kosong", function () {
    const response = pm.response.json();
    pm.expect(response.length).to.be.greaterThan(0);
});
```

### Response Time Validation

```javascript
pm.test("Response time kurang dari 1000 ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(1000);
});
```

### Response Field Validation

```javascript
pm.test("Title harus sesuai", function () {
    const response = pm.response.json();
    pm.expect(response.title).to.eql("QA API Testing");
});
```

## 📋 Example Request Body

### POST - Create New Post

```json
{
    "title": "QA API Testing",
    "body": "Testing API menggunakan Postman",
    "userId": 1
}
```

### PUT - Update Post

```json
{
    "id": 1,
    "title": "Update",
    "body": "Data berhasil diupdate",
    "userId": 1
}
```

### PATCH - Update Title

```json
{
    "title": "Title Updated dengan PATCH"
}
```

## ▶️ How to Run

### 1. Install Newman

Make sure Node.js and npm are installed.

```bash
npm install -g newman
```

Check Newman installation:

```bash
newman -v
```

### 2. Install Newman HTML Extra Reporter

```bash
npm install -g newman-reporter-htmlextra
```

### 3. Run Postman Collection

```bash
newman run "collection/API Testing - JSONPlaceholder.postman_collection.json"
```

### 4. Generate HTML Report

```bash
newman run "collection/API Testing - JSONPlaceholder.postman_collection.json" -r htmlextra
```

### 5. Generate Report with Custom File Name

```bash
newman run "collection/API Testing - JSONPlaceholder.postman_collection.json" -r htmlextra --reporter-htmlextra-export "reports/api-test-report.html"
```

## 📊 Test Result

The Newman test execution validates:

* HTTP status code
* JSON response format
* Response data
* Response fields
* Response time
* CRUD API operations

Example result:

```text
8 requests
8 assertions
0 failures
```

## 📄 Test Report

The HTML report is generated using **Newman HTML Extra Reporter**.

The report contains information about:

* Total requests
* Passed tests
* Failed tests
* Assertions
* Response time
* Request details
* Response details

Report location:

```text
reports/api-test-report.html
```

## 🎯 Testing Objective

The main objectives of this project are:

1. Verify API endpoints return the expected HTTP status codes.
2. Validate response format and response data.
3. Validate request and response fields.
4. Verify basic CRUD operations.
5. Create automated API tests using Postman.
6. Execute the Postman collection using Newman.
7. Generate an HTML automation test report.

