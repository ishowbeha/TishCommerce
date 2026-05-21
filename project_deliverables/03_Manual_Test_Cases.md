# Manual Test Cases - TishCommerce

---

## TECHNIQUE 1: BLACK BOX TESTING (15 Test Cases)

### Feature: Browse Products

| TC-ID | Description | Preconditions | Test Steps | Input Data | Expected Result | Actual Result | Status |
|-------|-------------|---------------|------------|------------|----------------|---------------|--------|
| TC-BB-01 | Verify products page loads correctly | App is running | 1. Navigate to http://localhost:3000/products | None | Product grid displays with products showing image, title, price | | |
| TC-BB-02 | Verify search functionality | Products page is loaded | 1. Type a product name in search box<br>2. Press Enter | "shoe" | Products matching "shoe" are shown; non-matching products are hidden | | |
| TC-BB-03 | Verify sort by price | Products page is loaded | 1. Click sort dropdown<br>2. Select "Sort by Price" | None | Products are sorted from lowest to highest price | | |
| TC-BB-04 | Verify category filter | Products page is loaded | 1. Click on a category filter | "Shoes" category | Only products in "Shoes" category are displayed | | |

### Feature: Product Details

| TC-BB-05 | Verify product detail page | Product exists | 1. Go to products page<br>2. Click on a product | None | Product detail page loads with image, title, price, description, "Add to Cart" button | | |
| TC-BB-06 | Verify "Add to Cart" button | Product detail page open | 1. Click "Add to Cart" button | None | Mini-cart appears showing added item; cart icon badge increments | | |

### Feature: Shopping Cart

| TC-BB-07 | Verify cart page shows items | Items in cart | 1. Navigate to /cart | None | Cart page lists all items with image, title, quantity, price, and total | | |
| TC-BB-08 | Verify remove item from cart | Items in cart | 1. Go to cart page<br>2. Click X button on an item | None | Item is removed from cart; total updates | | |
| TC-BB-09 | Verify cart empty message | Cart is empty | 1. Go to /cart | None | "Your cart is empty" message is displayed | | |

### Feature: Checkout

| TC-BB-10 | Verify checkout page loads | Items in cart | 1. Navigate to /checkout | None | Billing form, shipping method, payment method, and order summary sections are visible | | |

### Feature: Contact Form

| TC-BB-11 | Verify contact page loads | None | 1. Navigate to /contact | None | Contact form with Name, Email, Message fields and Send button is visible | | |

### Feature: Newsletter

| TC-BB-12 | Verify newsletter section is visible | Homepage loaded | 1. Scroll to bottom of homepage | None | Newsletter signup with email input and Subscribe button is visible | | |

### Feature: Navigation

| TC-BB-13 | Verify all menu links work | None | 1. Click on each menu item<br>2. Check URL changes | None | Each menu item navigates to correct page | | |
| TC-BB-14 | Verify social media links open | None | 1. Click on each social icon in header/footer | None | Each icon opens correct social media URL in new tab | | |

### Feature: Documentation

| TC-BB-15 | Verify documentation page | None | 1. Click "Docs" in menu | None | Documentation page loads with list of topics; clicking a topic shows content | | |

---

## TECHNIQUE 2: EQUIVALENCE PARTITIONING (10 Test Cases)

### Feature: Contact Form - Email Field

| TC-ID | Description | Preconditions | Test Steps | Input Data | Expected Result | Actual Result | Status |
|-------|-------------|---------------|------------|------------|----------------|---------------|--------|
| TC-EP-01 | Valid email format (valid partition) | Contact page loaded | 1. Enter valid email<br>2. Fill rest of form<br>3. Click Send | "user@example.com" | Form submits successfully | | |
| TC-EP-02 | Invalid email - no @ symbol (invalid partition) | Contact page loaded | 1. Enter email without @<br>2. Click Send | "userexample.com" | Validation error: "Please enter a valid email" | | |
| TC-EP-03 | Invalid email - no domain (invalid partition) | Contact page loaded | 1. Enter email without domain<br>2. Click Send | "user@" | Validation error: "Please enter a valid email" | | |
| TC-EP-04 | Empty email field (invalid partition) | Contact page loaded | 1. Leave email empty<br>2. Click Send | "" | Validation error: "Email is required" | | |

### Feature: Cart Quantity

| TC-EP-05 | Valid quantity of 1 (valid partition) | Product detail open | 1. Click "Add to Cart" | Quantity: 1 | Item added to cart with quantity 1 | | |
| TC-EP-06 | Valid quantity of 5 (valid partition) | Product detail open | 1. Add item once to cart<br>2. Go to cart<br>3. Click + button 4 times | Quantity: 5 | Quantity displays as 5; total = price × 5 | | |
| TC-EP-07 | Quantity of 0 attempted (invalid partition) | Items in cart | 1. Click - button when quantity is 1 | - | Item is removed (quantity cannot be 0) | | |

### Feature: Billing Form - Name Fields

| TC-EP-08 | Valid name (valid partition) | Checkout page | 1. Enter valid first name<br>2. Enter valid last name | "John", "Doe" | Fields accept input; no validation errors | | |
| TC-EP-09 | Empty first name (invalid partition) | Checkout page | 1. Leave first name empty<br>2. Try to place order | "" | Validation error: "First Name is required" | | |
| TC-EP-10 | Empty last name (invalid partition) | Checkout page | 1. Leave last name empty<br>2. Try to place order | "" | Validation error: "Last Name is required" | | |

---

## TECHNIQUE 3: BOUNDARY VALUE ANALYSIS (10 Test Cases)

### Feature: Product Quantity in Cart

| TC-ID | Description | Preconditions | Test Steps | Input Data | Expected Result | Actual Result | Status |
|-------|-------------|---------------|------------|------------|----------------|---------------|--------|
| TC-BV-01 | Minimum valid quantity: 1 | Product open | 1. Click "Add to Cart" once | Quantity: 1 | Item added with qty 1. Min boundary passes | | |
| TC-BV-02 | Below minimum: try qty 0 | Item in cart at qty 1 | 1. Click - button | - | Item removed. Below-minimum boundary handled correctly | | |
| TC-BV-03 | Large quantity: 99 | Item in cart | 1. Click + button 98 times | Quantity: 99 | Quantity updates to 99; total calculates correctly | | |
| TC-BV-04 | Very large quantity: 999 | Item in cart | 1. Add item many times | Quantity: 999 | System handles large number; total is price × quantity | | |

### Feature: Price Display

| TC-BV-05 | Product with $0.01 price (minimum) | Product exists | 1. Browse products<br>2. Find product with price 0.01 | Price: $0.01 | Price displays as "$0.01" correctly | | |
| TC-BV-06 | Product with $9999.99 price (maximum) | Product exists | 1. Browse products<br>2. Find product with large price | Price: $9999.99 | Price displays correctly with 2 decimal places | | |

### Feature: Total Calculation

| TC-BV-07 | Single item, qty 1, min price | Item in cart qty 1 | 1. Check cart total | 1 × $10.00 | Total = $10.00 | | |
| TC-BV-08 | Multiple items, varied quantities | Items in cart | 1. Add 2 items with different qty<br>2. Check total | Item1: qty 2 × $10 = $20<br>Item2: qty 3 × $15 = $45 | Total = $65.00 | | |

### Feature: Search Input

| TC-BV-09 | Search with single character | Products page | 1. Type "a" in search | "a" | Products containing "a" are shown | | |
| TC-BV-10 | Search with very long string (100+ chars) | Products page | 1. Type 100 characters in search | "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa" | Search handles long input gracefully; either shows results or empty state | | |

---

## TECHNIQUE 4: DECISION TABLE TESTING (8 Test Cases)

### Feature: Checkout - Payment and Shipping Combinations

| Condition | Rule 1 | Rule 2 | Rule 3 | Rule 4 |
|------------|--------|--------|--------|--------|
| Billing form completed? | Yes | Yes | No | Yes |
| Shipping method selected? | Yes | Yes | Yes | No |
| Payment method selected? | Yes | No | Yes | Yes |
| **Action: Place Order** | ✅ Success | ❌ Error | ❌ Error | ❌ Error |

| TC-ID | Description | Preconditions | Test Steps | Input Data | Expected Result | Actual Result | Status |
|-------|-------------|---------------|------------|------------|----------------|---------------|--------|
| TC-DT-01 | All fields completed (Rule 1 - Success) | Items in cart | 1. Complete billing form<br>2. Select shipping<br>3. Select PayPal<br>4. Click Place Order | All valid data | Order is processed; payment method shows | | |
| TC-DT-02 | No payment method (Rule 2 - Error) | Items in cart | 1. Complete billing<br>2. Select shipping<br>3. Don't select payment<br>4. Click Place Order | All fields complete except payment | Error message: "Please select a payment method" | | |
| TC-DT-03 | Billing form incomplete (Rule 3 - Error) | Items in cart | 1. Leave first name empty<br>2. Select shipping<br>3. Select PayPal<br>4. Click Place Order | Missing first name | Error message: "First Name is required" | | |
| TC-DT-04 | No shipping selected (Rule 4 - Error) | Items in cart | 1. Complete billing<br>2. Don't select shipping<br>3. Select payment<br>4. Click Place Order | No shipping | Error message: "Please select a shipping method" | | |

### Feature: Cart Operations Decision Table

| Condition | Rule 1 | Rule 2 | Rule 3 | Rule 4 |
|------------|--------|--------|--------|--------|
| Cart has items? | No | Yes | Yes | Yes |
| Click "Add to Cart"? | Yes | Yes | No | No |
| Click "Remove from Cart"? | No | No | Yes | Yes (last item) |
| **Action Result** | ✅ Add succeeds | ✅ Add succeeds; qty increments | ✅ Item removed | ❌ Cart is empty |

| TC-DT-05 | Add to empty cart | Empty cart | 1. Click "Add to Cart" on a product | None | Item added; cart badge shows 1 | | |
| TC-DT-06 | Add to existing cart | Cart has 1 item | 1. Click "Add to Cart" on same product | None | Quantity increments to 2 | | |
| TC-DT-07 | Remove one item from multi-item cart | Cart has 3 items | 1. Remove one item | None | Item removed; 2 items remain in cart | | |
| TC-DT-08 | Remove last item | Cart has 1 item | 1. Remove the last item | None | Cart becomes empty; "Your cart is empty" message shows | | |

---

## TECHNIQUE 5: STATE TRANSITION TESTING (10 Test Cases)

### Feature: Shopping Cart State Machine

**States:**
- S1: Empty Cart (no items)
- S2: Active Cart (1+ items)
- S3: Checkout in Progress
- S4: Order Completed

**Transitions:**
- T1: S1 → S2 (Add first item)
- T2: S2 → S2 (Add another item / Remove item but still have items)
- T3: S2 → S1 (Remove last item)
- T4: S2 → S3 (Click "Proceed to Checkout")
- T5: S3 → S2 (Go back from checkout)
- T6: S3 → S4 (Complete payment)
- T7: S4 → S1 (Order complete - cart becomes empty)

```
[S1: Empty Cart] ──T1──→ [S2: Active Cart]
[S2: Active Cart] ──T2──→ [S2: Active Cart]
[S2: Active Cart] ──T3──→ [S1: Empty Cart]
[S2: Active Cart] ──T4──→ [S3: Checkout]
[S3: Checkout]    ──T5──→ [S2: Active Cart]
[S3: Checkout]    ──T6──→ [S4: Order Complete]
[S4: Order Complete] ──T7──→ [S1: Empty Cart]
```

| TC-ID | Description | From State | Transition | Test Steps | Expected Result | Actual Result | Status |
|-------|-------------|------------|------------|-------------|----------------|---------------|--------|
| TC-ST-01 | Add first item (empty → active) | S1 | T1 | 1. Open any product<br>2. Click "Add to Cart" | S2: Cart shows 1 item; badge updates | | |
| TC-ST-02 | Add another item (active → active) | S2 | T2 | 1. Add another product to cart | S2: Cart now has 2 items | | |
| TC-ST-03 | Remove last item (active → empty) | S2 | T3 | 1. Open cart<br>2. Remove the only remaining item | S1: Cart is empty; "Your cart is empty" message | | |
| TC-ST-04 | Proceed to checkout (active → checkout) | S2 | T4 | 1. Open cart with items<br>2. Click "Proceed to Checkout" | S3: Checkout page loads billing form | | |
| TC-ST-05 | Go back from checkout (checkout → active) | S3 | T5 | 1. On checkout page<br>2. Click browser back button | S2: Back on cart page with items intact | | |
| TC-ST-06 | Complete payment (checkout → order complete) | S3 | T6 | 1. Complete checkout form<br>2. Process payment | S4: Order summary page shows confirmation | | |
| TC-ST-07 | Add item then remove immediately | S1 → S2 → S1 | T1 + T3 | 1. Add product to cart<br>2. Immediately go to cart<br>3. Remove the item | S1: Cart is empty | | |
| TC-ST-08 | Multiple add/remove cycles | S1 → S2 → S1 → S2 | T1 + T3 + T1 | 1. Add item<br>2. Remove item<br>3. Add item again | S2: Cart has 1 item (freshly added) | | |
| TC-ST-09 | Add same product twice | S1 → S2 | T1 (twice) | 1. Add product<br>2. Add same product again | S2: Quantity = 2 (not duplicate entry) | | |
| TC-ST-10 | Start checkout with empty cart | S1 | Direct /cart | 1. Navigate to /cart when empty | S1: "Your cart is empty" shown; no checkout button or checkout is disabled | | |

---

## SUMMARY: 53 TEST CASES TOTAL

| Technique | Count | TC IDs |
|-----------|-------|--------|
| Black Box Testing | 15 | TC-BB-01 to TC-BB-15 |
| Equivalence Partitioning | 10 | TC-EP-01 to TC-EP-10 |
| Boundary Value Analysis | 10 | TC-BV-01 to TC-BV-10 |
| Decision Table Testing | 8 | TC-DT-01 to TC-DT-08 |
| State Transition Testing | 10 | TC-ST-01 to TC-ST-10 |
| **TOTAL** | **53** | |

*Note: To complete these test cases, open the app at http://localhost:3000, execute each step, fill in the Actual Result and Status (Pass/Fail) columns, and document any bugs found in the Bug Report section.*