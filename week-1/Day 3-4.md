# Day 3–4: HTTP Basics

## Overview
HTTP (HyperText Transfer Protocol) is the foundation of communication on the web. Understanding its methods, status codes, and structure is crucial for working with APIs.

---

## HTTP Methods
HTTP methods define the actions that can be performed on a resource.

1. **GET**
   - Retrieve data from the server.
   - Example: Fetching a list of users.

2. **POST**
   - Send data to the server to create a resource.
   - Example: Creating a new user.

3. **PUT**
   - Update an existing resource on the server.
   - Example: Updating user information.

4. **DELETE**
   - Remove a resource from the server.
   - Example: Deleting a user.

---

## HTTP Status Codes
Status codes indicate the result of an HTTP request.

1. **2xx: Success**
   - 200 OK: The request was successful.
   - 201 Created: A resource was successfully created.

2. **3xx: Redirection**
   - 301 Moved Permanently: The resource has been moved to a new URL.

3. **4xx: Client Errors**
   - 400 Bad Request: The request was invalid.
   - 401 Unauthorized: Authentication is required.
   - 404 Not Found: The resource could not be found.

4. **5xx: Server Errors**
   - 500 Internal Server Error: The server encountered an error.

---

## Request and Response Structure

### Request
- **Headers**: Contain metadata (e.g., `Content-Type`, `Authorization`).
- **Body**: Contains data for POST or PUT requests.

### Response
- **Headers**: Provide metadata (e.g., `Content-Type`).
- **Body**: Contains the response data, often in JSON format.

---

## Interactive Exercise

### Task 1: Make HTTP Requests
1. Open Postman or any HTTP client.
2. Use the following public API: [JSONPlaceholder](https://jsonplaceholder.typicode.com).
3. Perform the following actions:
   - **GET**: Fetch a list of posts (`/posts`).
   - **POST**: Create a new post.
   - **PUT**: Update an existing post.
   - **DELETE**: Delete a post.

### Task 2: Analyze Status Codes
1. Make a request to a non-existent endpoint (`/invalid`).
2. Observe and analyze the returned status code.

---

## Summary
By the end of this session, you should:
- Understand HTTP methods and their use cases.
- Recognize common HTTP status codes and their meanings.
- Be able to structure HTTP requests and interpret responses.

---

## Additional Resources
- [HTTP Overview - Mozilla Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
- [JSONPlaceholder](https://jsonplaceholder.typicode.com)
