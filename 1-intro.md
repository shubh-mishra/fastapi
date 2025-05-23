# ⚡ What is FastAPI?

## 🚀 Overview

**FastAPI** is a **modern, fast (high-performance)** web framework for building APIs with **Python 3.7+** based on **standard Python type hints**.

It is designed to be:

- 🚀 **Fast**: Performance on par with Node.js and Go (thanks to Starlette and Pydantic)
- 💡 **Intuitive**: Great editor support with autocomplete and type checking
- 🧪 **Easy to test**: Built-in dependency injection system
- 📄 **Automatic docs**: OpenAPI (Swagger) and ReDoc generated automatically
- ⛑️ **Data validation**: Built-in request validation using Pydantic

---

## 🔧 Key Features

| Feature              | Description                                               |
|----------------------|-----------------------------------------------------------|
| **Fast performance** | Built on ASGI with `Starlette` and `uvicorn`              |
| **Type hints**       | Uses Python type hints for request parsing & validation   |
| **Pydantic**         | For data validation, parsing, and schema generation       |
| **Automatic docs**   | Swagger UI and ReDoc at `/docs` and `/redoc` endpoints    |
| **Dependency Injection** | Clean, testable, and modular code structure          |

---

## ✨ Hello World Example

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, World!"}
```
---

## 🔌 Run the server:
uvicorn main:app --reload

---

## Access:

* 📄 Docs: http://127.0.0.1:8000/docs
* 🔁 Endpoint: http://127.0.0.1:8000/

---

## 📦 Request with Validation

```python
from pydantic import BaseModel

class Item(BaseModel):
    name: str
    price: float
    is_offer: bool = False

@app.post("/items/")
def create_item(item: Item):
    return {"received_item": item}
```
---

## 🧱 Architecture Diagram

```sql
 Client (Browser/Postman)
         |
         V
   [ FastAPI App ]
         |
         |-- Routing (Path + Method)
         |-- Dependency Injection
         |-- Request Validation (Pydantic)
         |
         V
     Business Logic / DB / External APIs
```
---

## 📚 Summary

| Aspect          | Detail                                                |
| --------------- | ----------------------------------------------------- |
| **Framework**   | FastAPI                                               |
| **Built On**    | Starlette (ASGI), Pydantic                            |
| **Use Case**    | Building modern RESTful APIs                          |
| **Auto Docs**   | Swagger, ReDoc                                        |
| **Performance** | Very fast — among the top for Python frameworks       |
| **Ideal For**   | Data validation-heavy apps, microservices, async APIs |

---
