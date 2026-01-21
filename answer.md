# Hello
#  Lab: How the Web Works. 
## An Introduction to HTTP

**Course:** Intro to Web / ~Software Engineering~ 
**Topic:** HTTP, Requests, Responses, and Browsers  
**Estimated Time:** 45–60 minutes  
**Resources:**  
- MDN Web Docs, HTTP  
  https://developer.mozilla.org/en-US/docs/Web/HTTP  
- A modern browser
- Terminal access (macOS Terminal / Windows PowerShell / Linux shell)

---

## Part 1  What Is HTTP?

**Read:**  
MDN → *Overview of HTTP*  
https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview

### Questions

1. In **your own words**, what problem does HTTP solve?

   ```text
   Answer here: It solves how clients and servers interact with each other to successfully carry out a task.
   ```

2. According to MDN, HTTP is described as:
   - ☐ Stateful
   - ☐ Stateless

   What does this mean *in practice*?

   ```text
   Answer here: This means that there is no link between two requests being successively carried out on the same connection.
   ```

3. Fill in the blanks:

   > HTTP works as a **client–server** protocol, where a **client** sends a request and a **server** sends back a response.

---

##  Part 2 , HTTP Requests

### **Read:**  
MDN → *HTTP Messages (Requests/Responses)*  
https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages

### Questions

4. List **three components** of an HTTP request:

   ```text
   1. Method
   2. Request Target
   3. Protocol
   ```

5. What is the purpose of an HTTP **method**?

   ```text
   Answer here: It describes the meaning of the request and what the wanted outcome is.
   ```

6. Match the method to its most common use:

   | Method | Purpose |
   |------|--------|
   | GET | Recieve | 
   | POST | Send |
   | PUT | replace |
   | DELETE | delete |

---

## Part 3 , HTTP Responses

### **Read:**  
MDN → *HTTP Messages*  
https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages

### Questions

7. What information does an HTTP **status code** communicate?

   ```text
   Answer here: It is whether or not a specific request has been completed.
   ```

8. Categorize the following status codes:

   | Status Code | Category (2xx, 3xx, 4xx, 5xx) | Meaning |
   |------------|------------------------------|---------|
   | 200 | 2 | successful response |
   | 301 | 3| redirect - moved permanently |
   | 404 | 4 | not found |
   | 500 | 5 | internal server error|

9. Why is a **404 error** considered a *client-side* error?

   ```text
   Answer here: In most cases the URl is mistyped or pages that have been moved/deleted
   ```

---

## Part 4 , Using Browser Developer Tools

**Task: Inspect a Real HTTP Request**

1. Open your browser  
2. Visit: https://example.org  
3. Open **Developer Tools** (Right click → Inspect)  
4. Go to the **Network** tab  
5. Reload the page

### Data Collection

10. How many total requests were made when the page loaded?

   ```text
   Answer here: One
   ```

11. Click on the **HTML document request**. Fill in:

   | Field | Value |
   |------|------|
   | Request Method | GET |
   | Status Code | 304 Not Modified |
   | Content-Type | HTML |

12. Name **two headers** sent by the browser:

   ```text
   1. :authority
   2. :method
   ```

13. Name **two headers** sent by the server:

   ```text
   1. Age
   2. Allow
   ```

---

## Part 5 , `curl` 

**Goal:** Make HTTP requests *directly* from the command line and interpret the response.

> If `curl` is not available on your machine, ask your instructor for an alternative (or use a campus lab machine).  
> Just use codespaces!
> macOS/Linux typically have it installed by default. Windows 10/11 usually includes it too.

### Task A , Fetch a Page (Basic GET)

Run:

```bash
curl https://google.com
```

14. What kind of content did you receive (HTML, JSON, something else)? How can you tell?

```text
Answer here: HTML, it says the content type is html
```

### Task B , Show Response Headers (Inspect the Server Response)

Run:

```bash
curl -I https://google.com
```

15. Record the **status code** line (the one that starts with `HTTP/`):

```text
Answer here: 301
```

16. Record **two** response headers you see (write them exactly):

```text
1. date: Wed, 21 Jan 2026 16:45:53 GMT
2. cache-control: public, max-age=2592000
```

### Task C , Follow Redirects (3xx in Action)

Run:

```bash
curl -I http://google.com
```

17. Do you see a redirect (e.g., 301/302)? If yes, what is the `Location:` header pointing to?

```text
Answer here:http://google.com/
```

Now run the same request but **follow redirects**:

```bash
curl -IL http://google.com
```

18. How many distinct HTTP status lines do you see now? (Count the `HTTP/...` lines)

```text
Answer here: Two
```

### Task D , Compare GET vs HEAD

Run:

```bash
curl -I https://example.org
curl https://example.org
```

19. In your own words: what’s the difference between these two requests and their outputs?

```text
Answer here: The first one had a code of 301, moved permanently, and the second one was perfectly fine with a code of 200, OK.
```

---

## Part 6 , HTTP vs HTTPS

### **Read:**  
MDN → *HTTP Secure (HTTPS)*  
[https://developer.mozilla.org/en-US/docs/Glossary/HTTPS](https://developer.mozilla.org/en-US/docs/Glossary/HTTPS)

### Questions

20. What problem does HTTPS solve that HTTP does not?

```text
Answer here: It encrypts communication between a client an a server to allow a safe and secure connection between the two. 
```

21. What role does **encryption** play in HTTPS?

```text
Answer here: it secures the connection between the client and the server when dealing with sensitive date like banking or shopping.
```

---

## Reflection

22. Before this lab, you may have thought a web page was “just HTML.”  
After this lab, list **three things** that must happen *before* HTML appears on the screen.

```text
1. Method
2. request target
3. protocol
```

---

## Submission Checklist

- [ ] All questions answered  
- [ ] Developer Tools Data collected  
- [ ] `curl` outputs inspected (headers + redirects + HEAD vs GET)  
- [ ] Answerss  

---

## Optional

- Visit a different site (e.g., `https://www.wikipedia.org`)
- Compare:
  - Number of requests (DevTools)
  - Status codes
  - Resource types
