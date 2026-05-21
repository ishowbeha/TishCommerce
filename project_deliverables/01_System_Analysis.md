# System Analysis - TishCommerce E-Commerce Application

## 1. System Description

TishCommerce is a modern, database-free e-commerce web application built with Next.js 16, React 19, and Tailwind CSS. It allows customers to browse products, add items to a shopping cart, complete purchases via PayPal or Stripe, and contact the store. The application uses JSON configuration files instead of a database, making it lightweight and easy to deploy.

**Technology Stack:**
- Frontend: Next.js 16 + React 19 + Tailwind CSS
- State Management: Redux Toolkit
- Payments: PayPal SDK & Stripe
- Animations: Framer Motion
- Forms: Google reCAPTCHA v3

---

## 2. Actors

| Actor | Description |
|-------|-------------|
| **Customer** | A visitor who browses products, adds items to cart, completes checkout, and interacts with the store (contact form, newsletter) |
| **Payment Gateway (PayPal/Stripe)** | External system that processes payment transactions |
| **Email Service (Nodemailer)** | External system that sends contact form submissions and order confirmations |

*Note: There is no Admin/Registered User role in this system. There is no login or authentication.*

---

## 3. Functional Requirements (12 Functionalities)

| ID | Functionality | Description |
|----|---------------|-------------|
| FR-01 | View Homepage | Display banner, featured products, brand story, testimonials, newsletter signup, and brand logos |
| FR-02 | Browse Products | View all products with search, sort (name/price/newest), and category filtering |
| FR-03 | View Product Details | See individual product with images, price, description, and "Add to Cart" button |
| FR-04 | Manage Shopping Cart | Add/remove items, update quantities, view cart summary |
| FR-05 | Checkout Process | Complete billing form (name, address, country, city, postal code, shipping method) |
| FR-06 | PayPal Payment | Process payment via PayPal Express or PayPal Basket Express |
| FR-07 | Stripe Payment | Process payment via credit card through Stripe |
| FR-08 | View Order Summary | See confirmation after successful purchase |
| FR-09 | Contact Form | Submit name, email, and message with reCAPTCHA verification |
| FR-10 | Newsletter Signup | Subscribe with email address |
| FR-11 | Browse Documentation | View documentation/help pages |
| FR-12 | Navigation & Social Links | Navigate between pages via menu and follow social media links |

---

## 4. Use Case Diagram (Text Representation)

```
┌─────────────────────────────────────────────────┐
│               TishCommerce System                │
│                                                   │
│  ┌──────────────┐      ┌──────────────────┐      │
│  │              │      │                  │      │
│  │   Customer   │──────│ Browse Products  │      │
│  │              │      │                  │      │
│  └──────┬───────┘      └──────────────────┘      │
│         │                                         │
│         │    ┌─────────────────────────┐          │
│         ├────│ View Product Details    │          │
│         │    └─────────────────────────┘          │
│         │                                         │
│         │    ┌─────────────────────────┐          │
│         ├────│ Manage Shopping Cart    │          │
│         │    └─────────────────────────┘          │
│         │                                         │
│         │    ┌─────────────────────────┐          │
│         ├────│ Complete Checkout      │─────┐    │
│         │    └─────────────────────────┘     │    │
│         │                                    │    │
│         │    ┌─────────────────────────┐     │    │
│         ├────│ Make Payment (PayPal)   │◄────┤    │
│         │    └─────────────────────────┘     │    │
│         │                                    │    │
│         │    ┌─────────────────────────┐     │    │
│         ├────│ Make Payment (Stripe)   │◄────┤    │
│         │    └─────────────────────────┘          │
│         │                                         │
│         │    ┌─────────────────────────┐          │
│         ├────│ View Order Summary     │          │
│         │    └─────────────────────────┘          │
│         │                                         │
│         │    ┌─────────────────────────┐          │
│         ├────│ Submit Contact Form    │          │
│         │    └─────────────────────────┘          │
│         │                                         │
│         │    ┌─────────────────────────┐          │
│         ├────│ Subscribe to Newsletter│          │
│         │    └─────────────────────────┘          │
│         │                                         │
│         │    ┌─────────────────────────┐          │
│         └────│ Browse Documentation   │          │
│              └─────────────────────────┘          │
│                                                   │
│  ┌────────────────────────┐                       │
│  │   Payment Gateway      │◄──── (Extends Pay)   │
│  │   (PayPal/Stripe)      │                       │
│  └────────────────────────┘                       │
│                                                   │
│  ┌────────────────────────┐                       │
│  │   Email Service        │◄──── (Contact Form)  │
│  └────────────────────────┘                       │
└─────────────────────────────────────────────────┘
```

---

## 5. Detailed Use Cases (8 Use Cases)

### UC-01: Browse Products
| Field | Value |
|-------|-------|
| **Use Case ID** | UC-01 |
| **Actor** | Customer |
| **Description** | Customer browses the product catalog with search, sort, and filter options |
| **Preconditions** | Customer is on the Products page |
| **Main Flow** | 1. Customer navigates to /products<br>2. System displays all products in a grid<br>3. Customer can search by name<br>4. Customer can sort by name/price/newest<br>5. Customer can filter by category |
| **Postconditions** | Products are displayed according to selected filters |
| **Alternative Flow** | If no products match filters, show "No products found" message |

### UC-02: View Product Details
| Field | Value |
|-------|-------|
| **Use Case ID** | UC-02 |
| **Actor** | Customer |
| **Description** | Customer views detailed information about a specific product |
| **Preconditions** | Product exists in the system |
| **Main Flow** | 1. Customer clicks on a product from the grid<br>2. System navigates to /product/[slug]<br>3. System displays product image, title, price, description<br>4. Customer can click "Add to Cart" |
| **Postconditions** | Product details are displayed |

### UC-03: Add Item to Cart
| Field | Value |
|-------|-------|
| **Use Case ID** | UC-03 |
| **Actor** | Customer |
| **Description** | Customer adds a product to the shopping cart |
| **Preconditions** | Customer is viewing a product |
| **Main Flow** | 1. Customer clicks "Add to Cart"<br>2. System adds item to Redux cart state<br>3. System shows mini-cart notification<br>4. Cart badge updates with item count |
| **Postconditions** | Item is added to cart; cart counter increments |

### UC-04: Complete Checkout
| Field | Value |
|-------|-------|
| **Use Case ID** | UC-04 |
| **Actor** | Customer |
| **Description** | Customer fills in billing/shipping information and places order |
| **Preconditions** | Customer has items in cart and navigates to /checkout |
| **Main Flow** | 1. System loads billing form<br>2. Customer enters first name, last name, country, state, city, address1, address2, postal code<br>3. Customer selects shipping method<br>4. Customer selects payment method (PayPal or Stripe)<br>5. Customer clicks "Place Order"<br>6. System validates all required fields |
| **Postconditions** | Order is validated and ready for payment |
| **Alternative Flow** | If validation fails, show error message and highlight missing fields |

### UC-05: Pay with PayPal
| Field | Value |
|-------|-------|
| **Use Case ID** | UC-05 |
| **Actor** | Customer, Payment Gateway (PayPal) |
| **Description** | Customer completes payment using PayPal |
| **Preconditions** | Checkout form is completed and PayPal is selected |
| **Main Flow** | 1. System creates PayPal order via API<br>2. PayPal button renders<br>3. Customer clicks PayPal button<br>4. PayPal popup opens for login/approval<br>5. Customer approves payment<br>6. System captures order<br>7. System redirects to order summary |
| **Postconditions** | Payment is processed; order is confirmed |

### UC-06: Submit Contact Form
| Field | Value |
|-------|-------|
| **Use Case ID** | UC-06 |
| **Actor** | Customer |
| **Description** | Customer sends a message via the contact form |
| **Preconditions** | reCAPTCHA site key is configured |
| **Main Flow** | 1. Customer navigates to /contact<br>2. System loads contact form with reCAPTCHA<br>3. Customer enters name, email, and message<br>4. Customer clicks "Send Message"<br>5. System validates form and reCAPTCHA<br>6. System sends email via Nodemailer API<br>7. System shows success message |
| **Postconditions** | Message is sent to store owner |
| **Alternative Flow** | If reCAPTCHA fails or email sending fails, show error message |

### UC-07: Subscribe to Newsletter
| Field | Value |
|-------|-------|
| **Use Case ID** | UC-07 |
| **Actor** | Customer |
| **Description** | Customer subscribes to the store newsletter |
| **Preconditions** | Customer is on the homepage |
| **Main Flow** | 1. Customer scrolls to newsletter section<br>2. System displays email input and "Subscribe" button<br>3. Customer enters email address<br>4. Customer clicks "Subscribe"<br>5. System sends subscribe request via API<br>6. System shows confirmation |
| **Postconditions** | Email is subscribed to newsletter list |

### UC-08: Browse Documentation
| Field | Value |
|-------|-------|
| **Use Case ID** | UC-08 |
| **Actor** | Customer |
| **Description** | Customer views documentation/help pages |
| **Preconditions** | Documentation pages exist in config |
| **Main Flow** | 1. Customer clicks "Docs" in navigation<br>2. System navigates to /documentation<br>3. System lists available documentation pages<br>4. Customer clicks on a documentation topic<br>5. System shows the full documentation content |
| **Postconditions** | Documentation content is displayed |

---

## 6. Activity Diagram (Checkout Process)

```
┌────────────────────────────────────────────────────────┐
│            Activity: Complete Purchase                  │
├────────────────────────────────────────────────────────┤
│                                                        │
│  [Start]                                                │
│     │                                                   │
│     ▼                                                   │
│  ┌─────────────────────┐                               │
│  │ Navigate to Cart    │                               │
│  └──────────┬──────────┘                               │
│             │                                           │
│             ▼                                           │
│  ┌─────────────────────┐    ┌──────────────────┐       │
│  │ Review Cart Items   │───►│ Cart Empty?      │─────► │
│  └─────────────────────┘    └────────┬─────────┘       │
│                                      │                  │
│                                      │ (Items exist)    │
│                                      ▼                  │
│                               ┌─────────────────────┐   │
│                               │ Click "Proceed to   │   │
│                               │ Checkout"           │   │
│                               └──────────┬──────────┘   │
│                                          │              │
│                                          ▼              │
│                               ┌─────────────────────┐   │
│                               │ Fill Billing Form   │   │
│                               │ (Name, Address,     │   │
│                               │  Country, City, etc)│   │
│                               └──────────┬──────────┘   │
│                                          │              │
│                                          ▼              │
│                               ┌─────────────────────┐   │
│                               │ Select Shipping     │   │
│                               │ Method              │   │
│                               └──────────┬──────────┘   │
│                                          │              │
│                                          ▼              │
│                               ┌─────────────────────┐   │
│                               │ Select Payment      │   │
│                               │ Method              │   │
│                               └──────────┬──────────┘   │
│                                          │              │
│                              ┌───────────┴───────────┐  │
│                              │                       │  │
│                         [PayPal]               [Stripe] │
│                              │                       │  │
│                              ▼                       ▼  │
│                    ┌──────────────┐       ┌──────────┐  │
│                    │ PayPal       │       │ Stripe   │  │
│                    │ Popup/Login  │       │ Card Form│  │
│                    └──────┬───────┘       └─────┬────┘  │
│                           │                     │       │
│                           ▼                     ▼       │
│                    ┌──────────────────────────────┐     │
│                    │ Process Payment              │     │
│                    └──────────────┬───────────────┘     │
│                                   │                     │
│                            ┌──────┴──────┐              │
│                            │ Payment     │              │
│                            │ Successful? │              │
│                            └──────┬──────┘              │
│                               │         │               │
│                              Yes        No              │
│                               │         │               │
│                               ▼         ▼               │
│                    ┌─────────────┐  ┌──────────┐        │
│                    │ Show Order  │  │ Show     │        │
│                    │ Confirmation│  │ Error    │        │
│                    └─────────────┘  └──────────┘        │
│                                                        │
│  [End]                                                  │
└────────────────────────────────────────────────────────┘
```

---

## 7. Critical Functionalities for Testing

Based on risk analysis, the following are considered **critical**:

| Priority | Functionality | Risk |
|----------|--------------|------|
| **HIGH** | Checkout Process | Financial impact, data validation critical |
| **HIGH** | PayPal Payment | Financial transaction, external API dependency |
| **HIGH** | Stripe Payment | Financial transaction, external API dependency |
| **HIGH** | Shopping Cart | Core feature, data consistency critical |
| **MEDIUM** | Browse Products with Filters | User experience, search accuracy |
| **MEDIUM** | Contact Form | Data submission, reCAPTCHA integration |
| **LOW** | Documentation Pages | Static content, low risk |
| **LOW** | Navigation Links | Static links, low risk |