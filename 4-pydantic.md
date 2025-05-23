
# 🧱 What is Pydantic?

**Pydantic** is a **data validation and settings management library** for Python, based on **Python type annotations**. It is widely used in frameworks like **FastAPI** to validate request data.

---

## 🔍 Why Use Pydantic?

- ✅ Easy and automatic data validation
- 🔧 Automatic type coercion
- 📦 Built-in support for nested models
- 📄 JSON Schema generation
- ⚙️ Used for settings management with `.env` support

---

## 🚀 Getting Started

```bash
pip install pydantic
```

---

## 🧪 Basic Example

```python
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    email: str

user = User(id='1', name='Alice', email='alice@example.com')
print(user)
```

✅ Even though `id` is a string, Pydantic converts it to `int`.

---

## 🔧 Field Validation

```python
from pydantic import BaseModel, Field

class Product(BaseModel):
    name: str = Field(..., max_length=100)
    price: float = Field(gt=0)

product = Product(name="Laptop", price=1299.99)
```

---

## 🔁 Nested Models

```python
from typing import List

class Item(BaseModel):
    name: str
    quantity: int

class Order(BaseModel):
    items: List[Item]

order = Order(items=[{"name": "Book", "quantity": 2}])
```

---

## ⚙️ Custom Validators

```python
from pydantic import validator

class User(BaseModel):
    username: str

    @validator('username')
    def no_spaces(cls, v):
        if ' ' in v:
            raise ValueError('No spaces allowed')
        return v
```

---

## 📄 JSON Schema

```python
print(User.schema_json(indent=2))
```

Outputs a JSON schema representation of the model.

---

## 📁 Environment Settings Management

```python
from pydantic import BaseSettings

class Settings(BaseSettings):
    app_name: str
    debug: bool = False

    class Config:
        env_file = ".env"

settings = Settings()
```

---

## ✅ Summary

| Feature               | Description                                 |
|------------------------|---------------------------------------------|
| **Type Validation**   | Automatically validates and parses types    |
| **Type Coercion**     | Converts compatible types (e.g. str → int)  |
| **Nested Models**     | Supports deeply nested data structures      |
| **Custom Validators** | Add your own field-level validation logic   |
| **Environment Config**| Manages app settings via env vars           |
| **JSON Schema**       | Generates schemas for data models           |

---

## 🔗 Resources

- [Pydantic Documentation](https://docs.pydantic.dev/)
- [GitHub Repository](https://github.com/pydantic/pydantic)
