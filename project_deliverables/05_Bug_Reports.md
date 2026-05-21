# Bug Reports - TishCommerce (12 Bugs)

| Bug ID | Description | Steps to Reproduce | Expected Result | Actual Result | Severity | Priority | Screenshot |
|--------|-------------|-------------------|----------------|---------------|----------|----------|------------|
| BUG-01 | Image with modified width/height but not "auto" aspect ratio on brands | 1. Load homepage<br>2. Inspect brand images in browser console | Images should have consistent width/height attributes or auto aspect ratio | Console shows: "Image with src ... has either width or height modified, but not the other. If you use CSS to change the size of your image, also include the styles 'width: "auto"' or 'height: "auto"' to maintain the aspect ratio." | Low | Low | (Observed in browser console) |
| BUG-02 | Missing ALT text on product images | 1. Navigate to /products<br>2. Hover over product images<br>3. Check alt attributes | All product images should have descriptive ALT text for accessibility | Some product images may have empty or generic alt attributes | Medium | Medium | (Check product grid) |
| BUG-03 | Empty cart allows navigation to /checkout | 1. Ensure cart is empty<br>2. Navigate to http://localhost:3000/checkout | Checkout page should redirect to cart or show "cart is empty" message | Checkout page loads with empty form fields even with no cart items | Medium | High | (Screenshot of checkout with empty cart) |
| BUG-04 | reCAPTCHA error without proper configuration message | 1. Navigate to /contact when reCAPTCHA key is missing | Should show a user-friendly error message | Shows "Configuration Error" page with technical details instead of graceful degradation | Low | Medium | (Screenshot of error page) |
| BUG-05 | Products page shows "No products found" briefly before loading | 1. Navigate to /products<br>2. Observe initial load | Products should show immediately or show a loading spinner | Briefly shows "No products found" then loads products (flashing empty state) | Medium | Medium | (Observed during page load) |
| BUG-06 | Cart item quantity allows unlimited maximum | 1. Add product to cart<br>2. Go to /cart<br>3. Click + button many times | Quantity should have a reasonable upper limit (e.g., 99) | Quantity can be increased indefinitely, potentially causing UI/calculation issues | Low | Low | (Screenshot of quantity at 999+) |
| BUG-07 | Search does not handle special characters | 1. Go to /products<br>2. Type special characters like "@#$%" in search | Search should handle gracefully or show empty results | Possible unhandled characters causing unexpected behavior | Medium | Medium | (Test with special chars) |
| BUG-08 | Social media links open in same tab (security risk) | 1. Scroll to footer<br>2. Click any social media icon | Links should open in new tab with rel="noopener noreferrer" | Links may open in same tab (potential security/phishing risk) | Low | Low | (Check link behavior) |
| BUG-09 | Browser back button after adding to cart | 1. Browse product<br>2. Add to cart<br>3. Click browser back button | Should navigate to previous page | May cause unexpected behavior or stale cart state | Medium | Medium | (Observed during navigation) |
| BUG-10 | Missing form validation on newsletter email field | 1. Go to homepage<br>2. Scroll to newsletter<br>3. Enter invalid email "abc"<br>4. Click Subscribe | Should validate email format before submission | Invalid email may be accepted or show inconsistent validation | High | High | (Screenshot of newsletter section) |
| BUG-11 | Product price alignment issues on mobile | 1. Open dev tools (F12)<br>2. Resize to mobile width (375px)<br>3. View product grid | Prices should align properly on all screen sizes | Prices or elements may overflow or misalign on small screens | Medium | Medium | (Screenshot of mobile view) |
| BUG-12 | Accessibility: Missing focus indicators on interactive elements | 1. Navigate using Tab key through the site | All interactive elements should have visible focus outlines | Some buttons/links may lack visible focus indicators when tabbing | Medium | High | (Check with keyboard navigation) |

---

## Bug Severity & Priority Legend

| Severity | Description |
|----------|-------------|
| **Critical** | System crash, data loss, major feature broken |
| **High** | Major feature partially broken, no workaround |
| **Medium** | Feature works but with issues, has workaround |
| **Low** | Minor cosmetic issue,不影响 usability |

| Priority | Description |
|----------|-------------|
| **High** | Must fix before release |
| **Medium** | Should fix, can wait for next release |
| **Low** | Nice to fix when time allows |