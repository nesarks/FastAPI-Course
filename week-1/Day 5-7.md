# Day 5–7: Setting up FastAPI

## Overview
FastAPI is a modern, fast web framework for building APIs with Python. In this session, you'll set up your environment, install FastAPI, and run your first application.

---

## Step 1: Install Python
1. Download and install Python from [python.org](https://www.python.org/).
2. Verify the installation:
   ```bash
   python --version
   ```

---

## Step 2: Set Up a Virtual Environment
1. Create a project directory:
   ```bash
   mkdir fastapi-project
   cd fastapi-project
   ```
2. Create a virtual environment:
   ```bash
   python -m venv env
   ```
3. Activate the environment:
   - **Windows**: `.\env\Scripts\activate`
   - **Mac/Linux**: `source env/bin/activate`

---

## Step 3: Install FastAPI and Uvicorn
1. Install FastAPI:
   ```bash
   pip install fastapi
   ```
2. Install Uvicorn (ASGI server):
   ```bash
   pip install uvicorn
   ```

---

## Step 4: Create Your First FastAPI App
1. Create a file named `main.py`:
   ```python
   from fastapi import FastAPI

   app = FastAPI()

   @app.get("/")
   def read_root():
       return {"message": "Hello, FastAPI!"}
   ```
2. Run the application:
   ```bash
   uvicorn main:app --reload
   ```
3. Open your browser and visit `http://127.0.0.1:8000`.

---

## Step 5: Explore the Interactive API Docs
1. FastAPI automatically generates API documentation.
2. Visit:
   - Swagger UI: `http://127.0.0.1:8000/docs`
   - ReDoc: `http://127.0.0.1:8000/redoc`

---

## Interactive Exercise
1. Modify the `read_root` function to return a custom message.
2. Add a new route (`/hello/{name}`) that greets the user by name:
   ```python
   @app.get("/hello/{name}")
   def read_item(name: str):
       return {"message": f"Hello, {name}!"}
   ```

---

## Summary
By the end of this session, you should:
- Have a working FastAPI installation.
- Be able to create and run a basic FastAPI application.
- Understand how to use FastAPI's interactive documentation.

---

## Additional Resources
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Uvicorn Documentation](https://www.uvicorn.org/)
