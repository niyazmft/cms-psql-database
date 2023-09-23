# E-Commerce Database Schema Documentation

This documentation provides an overview of the database schema for an E-Commerce platform. The schema is designed to handle various aspects of an online retail business, including product management, order processing, user management, and more.

DBDigram.io URL: <toBeAdded>

## Tables

### Countries

- Stores information about countries.
- Fields:
  - `code`: Primary key, country code.
  - `name`: Name of the country.
  - `continent_name`: Name of the continent the country belongs to.

### Users

- Stores information about registered users.
- Fields:
  - `id`: Primary key, user ID.
  - `full_name`: User's full name.
  - `email`: User's email (unique).
  - `gender`: User's gender.
  - `date_of_birth`: User's date of birth.
  - `created_at`: Timestamp of user registration.
  - `country_code`: Foreign key, references the Countries table for user's country.
  - `billing_address_id`: Foreign key, references the Addresses table for billing address.
  - `shipping_address_id`: Foreign key, references the Addresses table for shipping address.

### Addresses

- Stores user addresses (billing and shipping).
- Fields:
  - `id`: Primary key, address ID.
  - `user_id`: Foreign key, references the Users table for address owner.
  - `address_type`: Type of address (billing or shipping).
  - `street_address`: Street address.
  - `city`: City.
  - `postal_code`: Postal code.
  - `country_code`: Foreign key, references the Countries table for address country.

### Merchants

- Represents merchant information.
- Fields:
  - `id`: Primary key, merchant ID.
  - `admin_id`: Foreign key, references the Users table for admin details.
  - `merchant_name`: Name of the merchant.
  - `country_code`: Foreign key, references the Countries table for merchant's country.
  - `created_at`: Timestamp of merchant registration.

### Products

- Stores information about available products.
- Fields:
  - `id`: Primary key, product ID.
  - `name`: Product name.
  - `merchant_id`: Foreign key, references the Merchants table for merchant details.
  - `price`: Product price.
  - `status`: Product status.
  - `created_at`: Timestamp of product creation.
  - `category_id`: Foreign key, references the Categories table for category information.
  - `description`: Product description.
  - `amazon_asin`: Unique identifier for Amazon.
  - `zalando_sku`: Unique identifier for Zalando.

### Categories

- Stores product categories.
- Fields:
  - `id`: Primary key, category ID.
  - `cat_name`: Category name.
  - `parent_id`: Foreign key, references itself to represent parent categories.

### Product Attributes

- Stores attributes associated with products.
- Fields:
  - `id`: Primary key, attribute ID.
  - `product_id`: Foreign key, references the Products table for product attributes.
  - `attribute_name`: Attribute name.
  - `attribute_value`: Attribute value.

### Product Variants

- Represents different variants of products.
- Fields:
  - `id`: Primary key, variant ID.
  - `product_id`: Foreign key, references the Products table for product variants.
  - `variant_name`: Variant name.
  - `price`: Variant price.
  - `stock_quantity`: Variant stock quantity.
  - `sku`: Variant SKU.
  - `amazon_asin`: ASIN for Amazon variant.
  - `zalando_sku`: SKU for Zalando variant.

### Product Images

- Stores image URLs for products.
- Fields:
  - `id`: Primary key, image ID.
  - `product_id`: Foreign key, references the Products table for product images.
  - `image_url`: Image URL.
  - `amazon_image_url`: Image URL for Amazon.
  - `zalando_image_url`: Image URL for Zalando.

### Product Categories

- Maps products to their categories.
- Fields:
  - `id`: Primary key, mapping ID.
  - `product_id`: Foreign key, references the Products table for product-category mapping.
  - `category_id`: Foreign key, references the Categories table for category information.
  - `amazon_category_id`: Category ID for Amazon.
  - `zalando_category_id`: Category ID for Zalando.

### Shipping Information

- Stores shipping details for products.
- Fields:
  - `id`: Primary key, shipping info ID.
  - `product_id`: Foreign key, references the Products table for shipping information.
  - `shipping_provider`: Shipping provider name.
  - `amazon_shipping_rate`: Shipping rate for Amazon.
  - `zalando_shipping_rate`: Shipping rate for Zalando.
  - `country_code`: Foreign key, references the Countries table for shipping country.

### Unique Identifiers

- Stores unique product identifiers (UPC, EAN, ISBN).
- Fields:
  - `id`: Primary key, identifier ID.
  - `product_id`: Foreign key, references the Products table for unique identifiers.
  - `upc`: Universal Product Code.
  - `ean`: European Article Number.
  - `isbn`: International Standard Book Number.

### Product Status

- Tracks product status on different marketplaces.
- Fields:
  - `id`: Primary key, status ID.
  - `product_id`: Foreign key, references the Products table for product status.
  - `amazon_status`: Status on Amazon (e.g., listed, out of stock).
  - `zalando_status`: Status on Zalando (e.g., listed, out of stock).

### Orders

- Stores information about customer orders.
- Fields:
  - `id`: Primary key, order ID.
  - `user_id`: Foreign key, references the Users table for order information.
  - `status`: Order status.
  - `created_at`: Timestamp of order creation.
  - `shipping_country_code`: Foreign key, references the Countries table for shipping country.
  - `payment_id`: Foreign key, references the Payments table for payment details.

### Order Items

- Represents items within each order.
- Fields:
  - `id`: Primary key, order item ID.
  - `order_id`: Foreign key, references the Orders table for order information.
  - `product_id`: Foreign key, references the Products table for product information.
  - `quantity`: Quantity of the product in the order.

### Payments

- Stores payment information associated with orders.
- Fields:
  - `id`: Primary key, payment ID.
  - `user_id`: Foreign key, references the Users table for payment details.
  - `amount`: Payment amount.
  - `payment_method`: Payment method.
  - `payment_status`: Payment status.
  - `created_at`: Timestamp of payment.

### Reviews

- Manages product reviews and ratings.
- Fields:
  - `id`: Primary key, review ID.
  - `product_id`: Foreign key, references the Products table for reviewed products.
  - `user_id`: Foreign key, references the Users table for reviewers.
  - `rating`: Product rating.
  - `review_text`: Review text.
  - `created_at`:

 Timestamp of review submission.

### Promotions

- Manages promotions, discounts, and coupon codes.
- Fields:
  - `id`: Primary key, promotion ID.
  - `code`: Promotion code (unique).
  - `discount_percentage`: Discount percentage.
  - `start_date`: Promotion start date.
  - `end_date`: Promotion end date.

### Promotions Users

- Associates users with promotions.
- Fields:
  - `id`: Primary key, association ID.
  - `user_id`: Foreign key, references the Users table for promotion users.
  - `promotion_id`: Foreign key, references the Promotions table for promotions.

### Returns

- Tracks return requests and processing.
- Fields:
  - `id`: Primary key, return request ID.
  - `order_id`: Foreign key, references the Orders table for return order.
  - `user_id`: Foreign key, references the Users table for return requester.
  - `reason`: Reason for return.
  - `return_status`: Return status.
  - `created_at`: Timestamp of return request.

### Inventory

- Manages product inventory, including batch tracking.
- Fields:
  - `id`: Primary key, inventory entry ID.
  - `product_id`: Foreign key, references the Products table for inventory tracking.
  - `batch_number`: Batch number.
  - `serial_number`: Serial number.
  - `quantity`: Quantity in stock.
  - `expiration_date`: Expiration date (if applicable).

### Roles

- Defines user roles for access control.
- Fields:
  - `id`: Primary key, role ID.
  - `role_name`: Role name (unique).

### User Roles

- Associates users with roles for access control.
- Fields:
  - `id`: Primary key, association ID.
  - `user_id`: Foreign key, references the Users table for user-role association.
  - `role_id`: Foreign key, references the Roles table for role definition.

### Audit Log

- Logs system activities and changes.
- Fields:
  - `id`: Primary key, log entry ID.
  - `user_id`: Foreign key, references the Users table for user-initiated actions.
  - `action`: Action performed.
  - `object_type`: Type of object affected.
  - `object_id`: ID of the affected object.
  - `timestamp`: Timestamp of the action.

### Translations

- Manages translations for internationalization.
- Fields:
  - `id`: Primary key, translation ID.
  - `language_code`: Language code.
  - `translation_key`: Translation key.
  - `translation_text`: Translated text.

### Search Filters

- Defines search and filtering options.
- Fields:
  - `id`: Primary key, filter ID.
  - `filter_name`: Filter name.
  - `filter_type`: Filter type.
  - `created_at`: Timestamp of filter creation.

### Analytics Data

- Stores various types of analytics data.
- Fields:
  - `id`: Primary key, data entry ID.
  - `data_type`: Type of data.
  - `data_value`: Data value.
  - `timestamp`: Timestamp of data entry.

### Email Templates

- Manages email templates for notifications.
- Fields:
  - `id`: Primary key, template ID.
  - `template_name`: Template name (unique).
  - `subject`: Email subject.
  - `body`: Email body.

### Email Queue

- Queues email notifications for sending.
- Fields:
  - `id`: Primary key, queue entry ID.
  - `user_id`: Foreign key, references the Users table for email recipients.
  - `template_id`: Foreign key, references the Email Templates table for email content.
  - `status`: Email status.
  - `sent_at`: Timestamp of email sending.

### API Access

- Manages API access and security.
- Fields:
  - `id`: Primary key, API access ID.
  - `user_id`: Foreign key, references the Users table for API access control.
  - `api_key`: API key (unique).

### Error Logs

- Records error messages and issues.
- Fields:
  - `id`: Primary key, log entry ID.
  - `user_id`: Foreign key, references the Users table for error origin.
  - `error_message`: Error message.
  - `error_type`: Type of error.
  - `occurred_at`: Timestamp of error occurrence.

## Table Groups

To improve visualization and organization, tables have been grouped into the following categories:

- `product_group`: Tables related to products.
- `user_group`: Tables related to users and addresses.
- `merchant_group`: Tables related to merchants.
- `payment_group`: Tables related to payments and promotions.
- `order_group`: Tables related to orders and returns.
- `other_group`: Miscellaneous tables.

This grouping simplifies the navigation and understanding of the schema.
