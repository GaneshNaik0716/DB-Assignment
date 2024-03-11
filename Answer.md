 From the above diagram, explain the relationship between the "Product" and "Product_Category" entities.?

 The relationship between the "Product" and "Product_Category" entities is one-to-many.
 where one product category can have multiple products, but each product belongs to only one category. 
 This relationship is represented by the foreign key constraint in the "Product" table: FOREIGN KEY (category_id) REFERENCES Product_Category(id)
 Here, the "category_id" column in the "Product" table references the "id" column in the "Product_Category" table, establishing a link between the two tables. 
 This means that each product record in the "Product" table must have a valid "category_id" that corresponds to an existing record in the "Product_Category" table.


 How could you ensure that each product in the "Product" table has a valid category assigned to it?
 
To ensure that each product in the "Product" table has a valid category assigned to it, you can utilize a foreign key constraint along with the NOT NULL constraint on the "category_id" column in the "Product" table. This ensures that every product must have a valid category assigned to it at insertion or update. Here's how you can modify the table creation script to include these constraints:
CREATE TABLE Product (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  description TEXT,
  SKU VARCHAR(50),
  category_id INT NOT NULL,
  inventory_id INT DEFAULT NULL,
  price DECIMAL(10,2) NOT NULL,
  discount_id INT DEFAULT NULL,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
  modified_at DATETIME DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP,
  deleted_at DATETIME DEFAULT NULL,
  FOREIGN KEY (category_id) REFERENCES Product_Category(id)
);
 The "category_id" column is NOT NULL and by adding the FOREIGN KEY constraint to reference the "id" column in the "Product_Category" table, you ensure that every product must have a valid category assigned to it. If an attempt is made to insert or update a product with an invalid category ID, it will result in a foreign key constraint violation error, preventing the operation from being completed.
