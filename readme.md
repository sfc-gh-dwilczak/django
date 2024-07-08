# Django / Snowflake Example
Here you will find a basic demo that I like to show to customers.

## Snowflake Setup
```sql
create schema raw.django;

CREATE TABLE product (
    id INT AUTOINCREMENT PRIMARY KEY,
    name VARCHAR(100),
    description VARCHAR(255),
    price DECIMAL(10, 2)
);

CREATE TABLE orders (
    id INT AUTOINCREMENT PRIMARY KEY,
    product_id INT,
    quantity INT,
    order_date DATE,
    FOREIGN KEY (product_id) REFERENCES product(id)
);

-- Inserting products
INSERT INTO product (name, description, price) VALUES
('Laptop', 'High-performance laptop', 1200.00),
('Smartphone', 'Latest model smartphone', 700.00),
('Headphones', 'Noise-cancelling headphones', 150.00);

-- Inserting orders
INSERT INTO orders (product_id, quantity, order_date) VALUES
(1, 1, CURRENT_DATE()),
(2, 2, CURRENT_DATE()),
(3, 3, CURRENT_DATE());

```

## Python Setup 

### Setup
```bash
python3 -m venv venv
source venv/bin/activate
pip3 install -r requirements.txt
```

### Start app
```bash
python manage.py runserver
```

### Api request
```bash
curl http://127.0.0.1:8000/api/products/
```