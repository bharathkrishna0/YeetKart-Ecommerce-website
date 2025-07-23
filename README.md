
# 🛍️ YeetCart

**YeetCart** is a minimalist yet functional e-commerce web app built with Flask and SQLite3. Designed to "yeet" your money at your favorite items, this platform covers everything from user registration to checkout — minus the payment gateway (for now!).

---

## 🔧 Features

* 🧑‍💻 User registration & login (with secure password hashing)
* 🛒 Add to cart, view cart, remove from cart
* 📦 Item details, quantity validation
* 👤 Profile page with password change
* ✅ Fake checkout with order validation
* 🙃 Friendly error (`apology.html`) and success pages

---


---

## 📦 Database Schema

All data is stored in `store.db`, which includes:

### 🧑 Customer Table

```sql
customer (
  id INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL,
  username TEXT NOT NULL,
  password TEXT NOT NULL, -- hashed!
  email TEXT NOT NULL,
  shipping_address TEXT
)
```

### 📦 Item Table

```sql
item (
  id INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL,
  name TEXT NOT NULL,
  description TEXT NOT NULL,
  quantity INTEGER NOT NULL,
  image TEXT NOT NULL, -- image path
  price REAL NOT NULL
)
```

### 📋 Orders Table

```sql
orders (
  id INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL,
  customer_id INTEGER NOT NULL,
  item_id INTEGER NOT NULL,
  sold_quantity INTEGER NOT NULL,
  time TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (customer_id) REFERENCES customer(id),
  FOREIGN KEY (item_id) REFERENCES item(id)
)
```

---

## 🚀 Key Routes (Flask)

| Route                             | Description                       |
| --------------------------------- | --------------------------------- |
| `/`                               | Home page showing all items       |
| `/register`                       | Register new users                |
| `/login`                          | Login existing users              |
| `/item/<int:item_id>`             | View item details                 |
| `/Addtocart`                      | Add item to user's cart           |
| `/cart`                           | Show all items in the user's cart |
| `/remove_from_cart/<int:item_id>` | Remove an item from the cart      |
| `/checkout`                       | Validate and "process" the order  |
| `/profile`                        | User info and password update     |
| `/change_password`                | Change user password              |
| `/logout`                         | Log out the user                  |

---

## ⚠️ Limitations

* No real payment integration yet — just vibes.
* No user sessions for cart persistence beyond login.
* Admin panel for adding items must be added manually or via DB.

---

## 💡 To Run Locally

1. Clone the repo:

   ```bash
   git clone https://github.com/yourusername/yeetcart.git
   cd yeetcart
   ```

2. Create and activate a virtual environment:

   ```bash
   python -m venv venv
   source venv/bin/activate  # or venv\Scripts\activate on Windows
   ```

3. Install Flask:

   ```bash
   pip install flask
   ```

4. Run the app:

   ```bash
   flask run
   ```

---

## 🎨 Screenshots

> Add screenshots here showing home page, cart, profile, etc. if desired.

---

## 🤓 Author

Made with 💸 by Bharath

---

