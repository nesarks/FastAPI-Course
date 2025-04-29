# Week 1: FastAPI Foundations - Deep Dive

## **Day 1: Understanding APIs and HTTP Basics**

### **What is an API?**
- An **API (Application Programming Interface)** allows two systems to talk to each other by exposing a set of rules or endpoints.
- Think of an API like a waiter in a restaurant:
  - The customer (you) makes a request (order food).
  - The waiter (API) takes the request to the kitchen (server).
  - The kitchen processes the request and sends a response (food) back to you.

#### **Why Use APIs?**
1. **Reusability**: APIs make it easy to reuse functionality across apps.
   - Example: Many websites use Google Maps API to display maps.
2. **Interoperability**: APIs allow different platforms to work together.
   - Example: You can log into websites using APIs from Google, Facebook, or GitHub.
3. **Scalability**: APIs simplify the process of integrating new features.

---

### **HTTP Basics**
HTTP (HyperText Transfer Protocol) is the foundation of communication on the web.

#### **Key HTTP Methods**
1. **GET**: Retrieve data.  
   Example: `GET /users` returns all users.
2. **POST**: Create new data.  
   Example: `POST /users` adds a new user.
3. **PUT/PATCH**: Update existing data.  
   Example: `PUT /users/1` updates the user with ID 1.
4. **DELETE**: Remove data.  
   Example: `DELETE /users/1` deletes the user with ID 1.

---

### **HTTP Status Codes**
Status codes tell you whether your request was successful:
- **2xx**: Success (e.g., `200 OK`, `201 Created`).
- **4xx**: Client errors (e.g., `400 Bad Request`, `404 Not Found`).
- **5xx**: Server errors (e.g., `500 Internal Server Error`).

#### **Headers**
Headers provide metadata about the request or response:
- `Content-Type: application/json` indicates the data format.
- `Authorization: Bearer <token>` is used for authentication.

---

### **Interactive Follow-Up Task**
1. **Activity**:  
   - Visit [Postman](https://www.postman.com/) or use `curl`/`httpie` to make a `GET` request to `https://jsonplaceholder.typicode.com/posts` (a public API). Observe the response.

2. **Design Challenge**:  
   - Imagine you’re building a Movie Rental API. Write down:
     - 3 routes (e.g., `/movies`, `/rent`, `/return`).
     - The HTTP method for each route.

---

## **Day 2: Setting Up FastAPI**

### **Installing FastAPI**
1. Install Python (3.9+ recommended).  
   Check your version:
   ```bash
   python --version
   ```
2. Create a project folder and navigate to it:
   ```bash
   mkdir fastapi-project && cd fastapi-project
   ```
3. Set up a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # macOS/Linux
   venv\Scripts\activate     # Windows
   ```
4. Install FastAPI and Uvicorn (a lightweight ASGI server):
   ```bash
   pip install fastapi uvicorn
   ```

---

### **Creating Your First FastAPI App**
1. Create a file named `main.py`:
   ```python
   from fastapi import FastAPI

   app = FastAPI()

   @app.get("/")
   def read_root():
       return {"message": "Hello, World!"}
   ```
2. Run the app:
   ```bash
   uvicorn main:app --reload
   ```
   - `main` refers to the file name (`main.py`).
   - `app` refers to the FastAPI instance.

3. Open your browser and visit `http://127.0.0.1:8000/` to see the response.

---

### **Interactive Follow-Up Task**
1. **Experiment**:  
   - Add another route `/welcome` that returns a message like `"Welcome to FastAPI!"`.

2. **Challenge**:  
   - Add metadata to your FastAPI app:
     ```python
     app = FastAPI(
         title="My First API",
         description="Learning FastAPI step by step",
         version="1.0.0"
     )
     ```

---

## **Day 3: Path Parameters in FastAPI**

### **What are Path Parameters?**
- Path parameters allow you to pass dynamic values in the URL.
- Example: `/users/{user_id}` accepts a `user_id` parameter.

---

### **Example: Path Parameters**
Add a route to retrieve a user by their ID:
```python
@app.get("/users/{user_id}")
def get_user(user_id: int):
    return {"user_id": user_id}
```
- If you visit `/users/42`, the response will be:
  ```json
  {"user_id": 42}
  ```

---

### **Interactive Follow-Up Task**
1. **Experiment**:  
   - Add a `/greet/{name}` route that returns `{"message": "Hello, {name}!"}`.

2. **Challenge**:  
   - Create a route `/math/{operation}/{x}/{y}` that performs basic math operations (`add`, `subtract`, `multiply`, `divide`) based on the `operation` parameter.

---

## **Day 4: Query Parameters in FastAPI**

### **What are Query Parameters?**
Query parameters allow optional inputs in the URL after the `?` symbol.

---

### **Example: Query Parameters**
Add a route to search for items:
```python
@app.get("/search")
def search_items(q: str = None, limit: int = 10):
    return {"query": q, "limit": limit}
```
- URL: `/search?q=FastAPI&limit=5`
- Response:
  ```json
  {"query": "FastAPI", "limit": 5}
  ```

---

### **Interactive Follow-Up Task**
1. **Experiment**:  
   - Add a `/books` route that accepts query parameters `title` and `author`.

2. **Challenge**:  
   - Create a `/weather` route that takes a `city` query parameter and returns a fake weather report for the city.

---

## **Day 5: Data Validation with Pydantic**

### **What is Pydantic?**
- Pydantic is a library used by FastAPI to validate incoming data.
- It ensures that the data matches the expected structure.

---

### **Example: Pydantic Models**
Define a model for an item:
```python
from pydantic import BaseModel

class Item(BaseModel):
    name: str
    price: float
    is_offer: bool = None

@app.post("/items/")
def create_item(item: Item):
    return item
```
- Example Request:
  ```json
  {
    "name": "Laptop",
    "price": 999.99,
    "is_offer": true
  }
  ```

---

### **Interactive Follow-Up Task**
1. **Experiment**:  
   - Modify the `Item` model to include a `description` field.

2. **Challenge**:  
   - Add validation to ensure the `name` field is at least 3 characters long.

---

## **Day 6: Interactive Documentation**

### **What is Interactive Documentation?**
FastAPI automatically generates:
1. **Swagger UI** (at `/docs`): Allows you to test APIs in the browser.
2. **ReDoc** (at `/redoc`): Provides an alternative documentation view.

---

### **Customizing API Metadata**
You can customize the title, description, and version:
```python
app = FastAPI(
    title="My Cool API",
    description="This API is built for learning purposes",
    version="1.0.0"
)
```

---

### **Interactive Follow-Up Task**
1. **Explore**:  
   - Open `/docs` and `/redoc` in your browser. Test all your routes.

2. **Challenge**:  
   - Add tags to your routes for better organization:
     ```python
     @app.get("/items", tags=["Items"])
     def get_items():
         return {"items": ["item1", "item2"]}
     ```

---

## **Day 7: Build a To-Do List API**

### **Project Objective**
Build a simple To-Do List API with the following features:
1. Add a task (`POST /tasks`).
2. View all tasks (`GET /tasks`).
3. View a specific task by ID (`GET /tasks/{task_id}`).

---

### **Step-by-Step Guide**
1. **Define a Pydantic Model**:
   ```python
   class Task(BaseModel):
       id: int
       name: str
       is_completed: bool = False
   ```

2. **Create Routes**:
   - Add a `POST` route to create tasks.
   - Add a `GET` route to retrieve all tasks.
   - Add a `GET` route to retrieve a task by ID.

---

### **Interactive Follow-Up Task**
1. **Extend**:  
   - Add a `PUT /tasks/{task_id}` route to mark a task as completed.

2. **Fun Task**:  
   - Add a `DELETE /tasks/{task_id}` route to delete a task.

---

## **By the End of Week 1**
- You will have built a fully functional To-Do List API.
- You’ll be familiar with HTTP basics, FastAPI routes, path/query parameters, and Pydantic models.