## Table Structure Overview

### 1. **Countries Table**
- Stores information about countries.
  - **code**: An integer representing the country code.
  - **name**: A string representing the name of the country.
  - **continent_name**: A string indicating the name of the continent to which the country belongs.

### 2. **Orders Table**
- Stores information about customer orders.
  - **id**: An integer representing the order ID.
  - **user_id**: An integer referring to the user placing the order.
  - **status**: A string representing the status of the order.
  - **created_at**: A string indicating the creation date of the order.
  - **shipping_country_code**: An integer referencing the shipping country code from the Countries table.
  - **payment_id**: An integer referencing the payment details from the Payments table.

### 3. **Order Items Table**
- Represents items within each order.
  - **id**: An integer representing the order item ID.
  - **order_id**: An integer referencing the order ID from the Orders table.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **quantity**: An integer indicating the quantity of the product ordered.

### 4. **Products Table**
- Stores information about available products.
  - **id**: An integer representing the product ID.
  - **name**: A string representing the name of the product.
  - **merchant_id**: An integer referencing the merchant details from the Merchants table.
  - **price**: An integer representing the price of the product.
  - **status**: A string indicating the status of the product.
  - **created_at**: A string indicating the creation date of the product.
  - **category_id**: An integer referencing the category information from the Categories table.
  - **description**: A text field providing a detailed description of the product.

### 5. **Users Table**
- Stores information about registered users.
  - **id**: An integer representing the user ID.
  - **full_name**: A string representing the full name of the user.
  - **email**: A string representing the email address of the user.
  - **gender**: A string representing the gender of the user.
  - **date_of_birth**: A string representing the date of birth of the user.
  - **created_at**: A string indicating the user's registration date.
  - **country_code**: An integer referencing the country details from the Countries table.
  - **billing_address_id**: An integer referencing the billing address details from the Addresses table.
  - **shipping_address_id**: An integer referencing the shipping address details from the Addresses table.

### 6. **Merchants Table**
- Represents merchant information.
  - **id**: An integer representing the merchant ID.
  - **admin_id**: An integer referencing the admin details from the Users table.
  - **merchant_name**: A string representing the name of the merchant.
  - **country_code**: An integer referencing the country details from the Countries table.
  - **created_at**: A string indicating the merchant's creation date.

### 7. **Categories Table**
- Stores product categories.
  - **id**: An integer representing the category ID.
  - **cat_name**: A string representing the name of the category.
  - **parent_id**: An integer referencing the parent category ID within the same table.

### 8. **Product Attributes Table**
- Stores attributes associated with products.
  - **id**: An integer representing the product attribute ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **attribute_name**: A string representing the name of the attribute.
  - **attribute_value**: A string representing the value of the attribute.

### 9. **Product Variants Table**
- Represents different variants of products.
  - **id**: An integer representing the product variant ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **variant_name**: A string representing the name of the product variant.
  - **price**: An integer representing the price of the product variant.
  - **stock_quantity**: An integer representing the available quantity in stock.
  - **sku**: A string representing the stock keeping unit of the product variant.

### 10. **Product Images Table**
- Stores image URLs for products.
  - **id**: An integer representing the image ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **image_url**: A string representing the URL of the image.

### 11. **Product Categories Table**
- Maps products to their categories.
  - **id**: An integer representing the product-category mapping ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **category_id**: An integer referencing the category ID from the Categories table.

### 12. **Shipping Information Table**
- Stores shipping details for products.
  - **id**: An integer representing the shipping information ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **shipping_provider**: A string representing the shipping provider.
  - **shipping_rate**: An integer representing the shipping rate.

### 13. **Unique Identifiers Table**
- Stores unique product identifiers (UPC, EAN, ISBN).
  - **id**: An integer representing the unique identifier ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **upc**: A string representing the Universal Product Code.
  - **ean**: A string representing the European Article Number.
  - **isbn**: A string representing the International Standard Book Number.

### 14. **Product Status Table**
- Tracks product status.
  - **id**: An integer representing the product status ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **status**: A string representing the status of the product.

### 15. **Payments Table**
- Stores payment information associated with orders.
  - **id**: An integer representing the payment ID.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **amount**: An integer representing the payment amount.
  - **payment_method**: A string representing the payment method used.
  - **payment_status**: A string representing the status of the payment.
  - **created_at**: A string indicating the date of the payment.

### 16. **Reviews Table**
- Manages product reviews and ratings.
  - **id**: An integer representing the review ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **rating**: An integer representing the rating given by the user.
  - **review_text**: A text field containing the review text.
  - **created_at**: A string indicating the date of the review.

### 17. **Promotions Table**
- Manages promotions, discounts, and coupon codes.
  - **id**: An integer representing the promotion ID.
  - **code**: A string representing the promotion code.
  - **discount_percentage**: An integer representing the discount percentage.
  - **start_date**: A string indicating the start

 date of the promotion.
  - **end_date**: A string indicating the end date of the promotion.

### 18. **Promotions Users Table**
- Associates users with promotions.
  - **id**: An integer representing the promotion user ID.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **promotion_id**: An integer referencing the promotion ID from the Promotions table.

### 19. **Returns Table**
- Tracks return requests and processing.
  - **id**: An integer representing the return ID.
  - **order_id**: An integer referencing the order ID from the Orders table.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **reason**: A text field providing the reason for the return request.
  - **return_status**: A string indicating the status of the return request.
  - **created_at**: A string indicating the date of the return request.

### 20. **Addresses Table**
- Stores user addresses (billing and shipping).
  - **id**: An integer representing the address ID.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **address_type**: A string indicating the type of address (billing or shipping).
  - **street_address**: A string representing the street address.
  - **city**: A string representing the city name.
  - **postal_code**: A string representing the postal code.
  - **country_code**: An integer referencing the country details from the Countries table.

### 21. **Inventory Table**
- Manages product inventory, including batch tracking.
  - **id**: An integer representing the inventory ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **batch_number**: A string representing the batch number.
  - **serial_number**: A string representing the serial number.
  - **quantity**: An integer representing the quantity in stock.
  - **expiration_date**: A string indicating the expiration date of the product batch.

### 22. **Brands Table**
- Stores information about brands.
  - **id**: An integer representing the brand ID.
  - **name**: A string representing the name of the brand.

### 23. **Sizes Table**
- Stores information about sizes.
  - **id**: An integer representing the size ID.
  - **name**: A string representing the size name.

### 24. **Shopping Cart Table**
- Manages items in the shopping cart.
  - **id**: An integer representing the shopping cart item ID.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **quantity**: An integer indicating the quantity of the product in the shopping cart.

### 25. **Wish List Table**
- Manages products in the wish list.
  - **id**: An integer representing the wish list item ID.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **product_id**: An integer referencing the product ID from the Products table.

### 26. **Discounts Table**
- Manages different types of discounts.
  - **id**: An integer representing the discount ID.
  - **name**: A string representing the name of the discount.
  - **description**: A text field providing a description of the discount.
  - **amount**: An integer representing the discount amount.

### 27. **Vouchers Table**
- Stores information about vouchers or coupons.
  - **id**: An integer representing the voucher ID.
  - **code**: A string representing the voucher code.
  - **description**: A text field providing a description of the voucher.
  - **discount_percentage**: An integer representing the discount percentage.

### 28. **Product Ratings Table**
- Manages ratings and reviews for products.
  - **id**: An integer representing the product rating ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **rating**: An integer representing the product rating.

### 29. **Product Tags Table**
- Stores tags or labels for products.
  - **id**: An integer representing the product tag ID.
  - **product_id**: An integer referencing the product ID from the Products table.
  - **tag_name**: A string representing the name of the tag.

### 30. **Roles Table**
- Defines user roles for access control.
  - **id**: An integer representing the role ID.
  - **role_name**: A string representing the name of the role.

### 31. **User Roles Table**
- Associates users with roles for access control.
  - **id**: An integer representing the user role ID.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **role_id**: An integer referencing the role ID from the Roles table.

### 32. **Audit Log Table**
- Logs system activities and changes.
  - **id**: An integer representing the audit log ID.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **action**: A string representing the action performed.
  - **object_type**: A string representing the type of object affected.
  - **object_id**: An integer representing the ID of the object affected.
  - **timestamp**: A string indicating the timestamp of the action.

### 33. **Email Templates Table**
- Manages email templates for notifications.
  - **id**: An integer representing the email template ID.
  - **template_name**: A string representing the name of the template.
  - **subject**: A string representing the subject of the email.
  - **body**: A text field containing the body of the email.

### 34. **Email Queue Table**
- Queues email notifications for sending.
  - **id**: An integer representing the email queue ID.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **template_id**: An integer referencing the email template ID from the Email Templates table.
  - **status**: A string representing the status of the email.
  - **sent_at**: A string indicating the timestamp when the email was sent.

### 35. **API Access Table**
- Manages API access and security.
  - **id**: An integer representing the API access ID.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **api_key**: A string representing the API key.

### 36. **Error Logs Table**
- Records error messages and issues.
  - **id**: An integer representing the error log ID.
  - **user_id**: An integer referencing the user ID from the Users table.
  - **error_message**: A text field containing the error message.
  - **error_type**: A string representing the type of error.
  - **occurred_at**: A string indicating the timestamp when the error occurred.

## Table Grouping

The tables have been logically grouped into several categories to provide a better understanding of their relationships and functionalities within the system. These groups include:

- **Product Group**
- **User Group**
- **Merchant Group**
- **Payment Group**
- **Order Group**
- **Additional Group**
- **Other Group**
