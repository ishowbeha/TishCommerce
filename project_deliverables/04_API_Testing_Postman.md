# API Testing - Postman Collection

## API Endpoints Available

| # | Method | Endpoint | Description |
|---|--------|----------|-------------|
| 1 | GET | `/api/localization` | Get all localization/settings data |
| 2 | GET | `/api/products` | Get all products |
| 3 | GET | `/api/products?slug=product-slug` | Get single product |
| 4 | POST | `/api/contact` | Submit contact form |
| 5 | POST | `/api/newsletter` | Subscribe to newsletter |
| 6 | POST | `/api/checkout` | Process checkout |
| 7 | POST | `/api/checkout/placeorder` | Place order |

## How to Use in Postman

1. **Open Postman**
2. Click **Import** → **Raw Text** → Paste each test below
3. Or create each request manually

---

## API Test Case 1: GET /api/localization

**Test ID:** API-TC-01
**Description:** Verify localization API returns store settings

**Postman Setup:**
- Method: `GET`
- URL: `http://localhost:3000/api/localization`
- Headers: None needed

**Expected Response (200):**
```json
{
  "siteName": "TishCommerce",
  "siteTagline": "Your Database-Free Store",
  "menu": [...],
  "labels": {...}
}
```

**To Test in Postman:**
1. Create a GET request to `http://localhost:3000/api/localization`
2. Click **Send**
3. Verify status: 200 OK
4. Verify `siteName` equals "TishCommerce"
5. Verify `menu` array has items

---

## API Test Case 2: GET /api/products

**Test ID:** API-TC-02
**Description:** Verify products API returns product list

**Postman Setup:**
- Method: `GET`
- URL: `http://localhost:3000/api/products`
- Headers: None needed

**Expected Response (200):**
```json
[
  {
    "ID": "...",
    "Title": "...",
    "Slug": "...",
    "SalePrice": "...",
    "RegularPrice": "...",
    "FeatureImageURL": "..."
  }
]
```

**To Test in Postman:**
1. Create a GET request to `http://localhost:3000/api/products`
2. Click **Send**
3. Verify status: 200 OK
4. Verify response is an array
5. Verify first product has `Title` and `Slug` fields

---

## API Test Case 3: GET /api/products?slug={product-slug}

**Test ID:** API-TC-03
**Description:** Verify single product endpoint

**Postman Setup:**
- Method: `GET`
- URL: `http://localhost:3000/api/products?slug=example-product`
- (Replace "example-product" with an actual slug from TC-02)

**Expected Response (200):**
```json
{
  "ID": "...",
  "Title": "...",
  "Slug": "example-product",
  "Description": "...",
  "SalePrice": "...",
  "FeatureImageURL": "..."
}
```

**Expected Response for Not Found (404):**
```json
{
  "error": "Product not found"
}
```

**To Test in Postman:**
1. First run API-TC-02 to get a valid slug
2. Create GET request with `?slug=VALID_SLUG`
3. Verify 200 OK and product data
4. Test with `?slug=nonexistent-product`
5. Verify 404 error response

---

## API Test Case 4: POST /api/newsletter

**Test ID:** API-TC-04
**Description:** Test newsletter subscription endpoint

**Postman Setup:**
- Method: `POST`
- URL: `http://localhost:3000/api/newsletter`
- Headers: `Content-Type: application/json`
- Body (raw JSON):

**Valid Request:**
```json
{
  "email": "testuser@example.com"
}
```

**Expected Response (200):**
```json
{
  "message": "Subscribed successfully"
}
```

**Invalid Request (empty email):**
```json
{
  "email": ""
}
```

**Expected Response (400):**
```json
{
  "error": "Email is required"
}
```

**To Test in Postman:**
1. Create POST request with valid email
2. Click **Send**
3. Verify response (may fail if Mailchimp not configured - status shows API behavior)
4. Test with empty email to see validation

---

## API Test Case 5: POST /api/contact

**Test ID:** API-TC-05
**Description:** Test contact form submission

**Postman Setup:**
- Method: `POST`
- URL: `http://localhost:3000/api/contact`
- Headers: `Content-Type: application/json`
- Body (raw JSON):

**Valid Request:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "message": "This is a test message.",
  "token": "test-token"
}
```

**Expected Response if reCAPTCHA configured (200):**
```json
{
  "success": true
}
```

**Expected Response if missing reCAPTCHA (400):**
```json
{
  "success": false,
  "message": "Missing reCAPTCHA token. Please refresh the page and try again."
}
```

**Missing Fields Test:**
```json
{
  "name": "",
  "email": "",
  "message": "",
  "token": ""
}
```

**Expected Response (400):**
```json
{
  "success": false,
  "message": "Missing required fields."
}
```

**To Test in Postman:**
1. Create POST request with all fields
2. Click **Send**
3. Verify error handling works correctly
4. Test with missing fields to verify validation

---

## API Test Results Summary

| TC-ID | Endpoint | Method | Status | Notes |
|-------|----------|--------|--------|-------|
| API-TC-01 | /api/localization | GET | ☐ | Should always return 200 |
| API-TC-02 | /api/products | GET | ☐ | Should always return 200 |
| API-TC-03 | /api/products?slug=X | GET | ☐ | 200 for valid slug, 404 for invalid |
| API-TC-04 | /api/newsletter | POST | ☐ | 400 for missing email |
| API-TC-05 | /api/contact | POST | ☐ | 400 for missing fields |

---

## Postman Export (JSON) Instructions

To save your Postman collection:
1. In Postman, create a **Collection** called "TishCommerce API Tests"
2. Add all 5 requests to it
3. Click the **...** menu on the collection
4. Select **Export**
5. Save the `.json` file to: `project_deliverables/postman_collection.json`