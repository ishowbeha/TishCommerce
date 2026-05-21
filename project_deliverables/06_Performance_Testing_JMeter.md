# Performance Testing - Apache JMeter

## How to Run JMeter
1. Navigate to the folder where you extracted JMeter (e.g., `C:\JMeter\apache-jmeter-5.6.3\bin\`)
2. Double-click `jmeter.bat`
3. JMeter GUI will open

---

## Test Plan 1: Homepage Load Test

### Test Configuration
- **Threads (Users):** 10 concurrent users
- **Ramp-Up Period:** 5 seconds
- **Loop Count:** 3
- **Total Requests:** 30 (10 users × 3 loops)

### Steps to Create in JMeter:

1. **Add Thread Group:**
   - Right-click "Test Plan" → Add → Threads (Users) → Thread Group
   - Set: Number of Threads = 10
   - Set: Ramp-up period = 5
   - Set: Loop Count = 3

2. **Add HTTP Request Defaults:**
   - Right-click "Thread Group" → Add → Config Element → HTTP Request Defaults
   - Set: Protocol = `http`
   - Set: Server Name = `localhost`
   - Set: Port Number = `3000`

3. **Add HTTP Request:**
   - Right-click "Thread Group" → Add → Sampler → HTTP Request
   - Set: Path = `/`

4. **Add Listeners:**
   - Right-click "Thread Group" → Add → Listener → **Summary Report**
   - Right-click "Thread Group" → Add → Listener → **View Results Tree**
   - Right-click "Thread Group" → Add → Listener → **Graph Results**

### Expected Metrics:
| Metric | Expected Value |
|--------|---------------|
| Average Response Time | < 500ms |
| Min Response Time | < 100ms |
| Max Response Time | < 2000ms |
| Error Rate | 0% |
| Throughput | > 50 requests/min |

---

## Test Plan 2: Multi-Page Navigation Test

### Test Configuration
- **Threads (Users):** 5 concurrent users
- **Ramp-Up Period:** 10 seconds
- **Loop Count:** 2

### HTTP Requests (in order for each user):
1. `/` (Homepage)
2. `/products` (Products page)
3. `/cart` (Cart page)
4. `/contact` (Contact page)
5. `/documentation` (Documentation page)

### Steps:
1. Create a new Thread Group
2. Add 5 HTTP Request samplers under it
3. Set paths as listed above
4. Add Summary Report and View Results Tree listeners

### Expected Metrics:
| Metric | Expected Value |
|--------|---------------|
| Average Response Time | < 1000ms |
| Error Rate | 0% |
| Throughput | > 30 requests/min |

---

## Test Plan 3: API Performance Test

### Test Configuration
- **Threads (Users):** 20 concurrent users
- **Ramp-Up Period:** 10 seconds
- **Loop Count:** 1

### HTTP Requests:
1. `GET /api/localization`
2. `GET /api/products`

### Steps:
1. Create a new Thread Group
2. Add 2 HTTP Request samplers for each API endpoint
3. Add Summary Report listener

### Expected Metrics:
| Metric | Expected Value |
|--------|---------------|
| Average Response Time | < 300ms |
| Error Rate | 0% |
| Throughput | > 100 requests/min |

---

## Performance Test Results Template

### Test 1: Homepage Load Test Results

| Metric | Value |
|--------|-------|
| Total Requests Made | ☐ |
| Average Response Time | ☐ ms |
| Min Response Time | ☐ ms |
| Max Response Time | ☐ ms |
| Error Rate | ☐ % |
| Throughput | ☐ req/min |

### Test 2: Multi-Page Navigation Results

| Page | Average Response Time | Error Rate |
|------|---------------------|------------|
| Homepage (/) | ☐ ms | ☐ % |
| Products (/products) | ☐ ms | ☐ % |
| Cart (/cart) | ☐ ms | ☐ % |
| Contact (/contact) | ☐ ms | ☐ % |
| Documentation (/documentation) | ☐ ms | ☐ % |

### Test 3: API Performance Results

| Endpoint | Average Response Time | Error Rate |
|----------|---------------------|------------|
| /api/localization | ☐ ms | ☐ % |
| /api/products | ☐ ms | ☐ % |

---

## Analysis

Based on test results, answer the following:

1. **Is response time acceptable?** (< 1 second for pages, < 300ms for APIs)
2. **Are there any errors?** (0% error rate expected)
3. **Can the system handle concurrent users?** (10-20 users)
4. **Which page is the slowest?** (Identify bottleneck)
5. **Recommendations for improvement?** (e.g., caching, code optimization)