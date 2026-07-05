# Application Programming Interface (API)

## 1. Why do we need APIs?

In the previous chapter, we learned how clients and servers communicate using **HTTP** and **HTTPS**.

The communication flow looks like this:

```text
Client
   │
HTTP Request
   │
   ▼
Server
```

Now another important question arises.

The client knows how to communicate using HTTP.

But,

**how does it know what functionality the server provides?**

For example,

- How does Instagram know how to load your feed?
- How does YouTube know how to search videos?
- How does Swiggy know how to fetch nearby restaurants?
- How does Google Maps know how to calculate directions?

The client cannot directly access the server's database or internal code.

Instead,

it communicates with the server through **APIs**.

APIs provide a safe and organized way for applications to communicate with each other.

Almost every modern application you use today relies on APIs.

---

## 2. What is an API?

API stands for **Application Programming Interface**.

An API is a **set of rules that allows different software applications to communicate with each other.**

Think of an API as a **contract** between the client and the server.

The API clearly defines:

- What requests the client can send.
- What data the client should provide.
- What response the server will return.

The client doesn't need to know how the server works internally.

It only needs to know how to use the API.

---

## 3. What Problem Does It Solve?

Imagine if every mobile application directly connected to a database.

```text
Mobile App
      │
      ▼
Database
```

This would create many problems.

- Anyone could access the database.
- Sensitive information could be exposed.
- Every application would need to understand the database structure.
- Changing the database would break all applications.

Instead,

applications communicate through APIs.

```text
Client
   │
   ▼
API
   │
   ▼
Database
```

The API controls:

- Who can access data.
- What data can be accessed.
- What operations are allowed.

This makes applications more secure, scalable, and easier to maintain.

---

## 4. Real-Life Analogy

Imagine you visit a restaurant.

You don't enter the kitchen and cook your own food.

Instead,

you place your order with the waiter.

```text
Customer
     │
     ▼
Waiter
     │
     ▼
Kitchen
```

The waiter:

- Takes your order.
- Delivers it to the kitchen.
- Brings your food back.

You never interact directly with the chef.

Similarly,

- Customer → Client
- Waiter → API
- Kitchen → Server
- Ingredients → Database

The API acts like the waiter.

It carries requests from the client to the server and brings the response back.

---

## 5. How Does an API Work?

Let's understand this using Instagram.

### Step 1

You open Instagram.

### Step 2

You refresh your feed.

### Step 3

The Instagram app sends an HTTP request to the **Feed API**.

```http
GET /feed
```

### Step 4

The API receives the request.

### Step 5

The API checks whether you are authenticated.

### Step 6

If authentication is successful,

the API communicates with the database.

### Step 7

The database returns your posts.

### Step 8

The API converts the data into JSON.

### Step 9

The API sends the JSON response back to the Instagram app.

### Step 10

The Instagram app displays your feed.

Notice something important.

The Instagram app never communicates directly with the database.

Everything goes through the API.

---

## 6. Step-by-Step Request Flow

```text
User Opens Instagram
        │
        ▼
Instagram App
        │
HTTP Request
        ▼
Feed API
        │
Business Logic
        ▼
Database
        │
Returns Data
        ▼
Feed API
        │
JSON Response
        ▼
Instagram App
        │
Displays Feed
```

---

## 7. API Requests

Whenever a client wants something from the server,

it sends an API request.

An API request usually contains:

- URL (Endpoint)
- HTTP Method
- Headers
- Optional Request Body

Example:

```http
GET /feed
Host: api.instagram.com
Authorization: Bearer Token
```

The API reads the request and decides what action should be performed.

---

## 8. API Responses

After processing the request,

the API sends a response back to the client.

A response usually contains:

- Status Code
- Response Headers
- Response Body

Most modern APIs return data in **JSON** format because it is lightweight and easy for applications to understand.

Example:

```json
{
  "username": "john",
  "posts": 25
}
```

The client reads this response and displays the information to the user.

## 9. Inputs and Outputs

Every API accepts some input and returns an output.

If the input is correct,

the API processes the request and returns the expected result.

If the input is incorrect,

the API returns an error message.

Let's understand this with a few examples.

### Weather API

Input:

```text
City = Bangalore
```

Output:

```json
{
  "city": "Bangalore",
  "temperature": 30,
  "condition": "Sunny"
}
```

---

### Google Maps API

Input:

```text
Destination = Mysore Palace
```

Output:

```json
{
  "distance": "145 km",
  "duration": "3 Hours"
}
```

---

### Calculator API

Input:

```text
5 + 10
```

Output:

```text
15
```

Every API clearly defines:

- What input it accepts.
- What output it returns.

This predictable behavior makes APIs easy for applications to use.

---

## 10. API Response Formats

When an API returns data,

it needs to follow a structured format that both the client and server understand.

The two most common response formats are:

### JSON (JavaScript Object Notation)

JSON is the most widely used API response format today.

It is lightweight,

easy to read,

and supported by almost every programming language.

Example:

```json
{
  "name": "John",
  "age": 24,
  "city": "Bangalore"
}
```

Most modern REST APIs use JSON.

---

### XML (eXtensible Markup Language)

Before JSON became popular,

many APIs used XML.

Example:

```xml
<user>
    <name>John</name>
    <age>24</age>
</user>
```

XML is still used in some enterprise applications,

but JSON is the preferred choice for modern web applications.

---

## 11. Types of APIs

Not all APIs are meant for the same purpose.

Depending on who can access them,

APIs are divided into different types.

---

### Public APIs (Open APIs)

Public APIs are available for external developers.

Anyone with permission can use them.

Examples:

- Google Maps API
- GitHub API
- OpenWeather API
- YouTube Data API

These APIs allow developers to build applications on top of existing services.

---

### Private APIs (Internal APIs)

Private APIs are used only inside an organization.

External developers cannot access them.

Example:

Inside Amazon,

different internal services communicate using private APIs.

Customers never interact with these APIs directly.

---

### Partner APIs

Partner APIs are shared only with trusted business partners.

Access is usually provided through agreements and authentication.

Example:

A payment gateway providing APIs to e-commerce companies.

---

### Library APIs

Not all APIs communicate over the Internet.

Programming languages also provide APIs.

Example:

Python's built-in list methods.

```python
numbers.sort()

fruits.append("Orange")
```

Here,

`sort()` and `append()` are also APIs.

They provide predefined functionality for developers.

---

## 12. Where Do APIs Live?

Many beginners think APIs are separate applications.

In reality,

most APIs are part of the backend application.

A typical architecture looks like this:

```text
Client
   │
HTTP Request
   ▼
Backend Server
   │
 ┌─────────────┐
 │     API     │
 └─────────────┘
   │
Business Logic
   │
Database
```

The API runs inside the backend server.

It receives requests,

executes business logic,

communicates with the database,

and returns responses.

The API is not usually a separate machine.

It is simply one part of the backend application.

---

## 13. How Modern Applications Use APIs

Most modern applications are not powered by a single API.

Instead,

they use many APIs working together.

Let's take Uber as an example.

When you book a ride,

multiple APIs work behind the scenes.

```text
Uber App
     │
     ├── Authentication API
     │
     ├── Maps API
     │
     ├── Ride Matching API
     │
     ├── Payment API
     │
     └── Notification API
```

Each API performs one specific task.

Together,

they provide a complete user experience.

The same approach is used by many companies.

### Instagram

- Login API
- Feed API
- Stories API
- Comments API
- Notification API

---

### Amazon

- Product API
- Cart API
- Payment API
- Order API
- Delivery API

---

### Netflix

- Authentication API
- Recommendation API
- Search API
- Streaming API

Instead of building one huge application,

companies divide functionality into smaller APIs.

This makes applications easier to develop,

maintain,

and scale.

---

## 14. Real-World API Examples

You interact with APIs every day,

even if you don't realize it.

### Google Maps API

Provides maps,

directions,

and navigation.

---

### Weather API

Returns weather information for a given city.

---

### Stripe API

Processes online payments securely.

---

### Razorpay API

Allows businesses to accept online payments.

---

### GitHub API

Allows applications to access repositories,

issues,

commits,

and pull requests.

---

### OpenAI API

Allows developers to integrate AI features into their applications.

---

### Twilio API

Enables applications to send SMS messages,

make phone calls,

and send verification codes.

## 15. API Authentication (Introduction)

Not every API should be accessible to everyone.

Imagine your banking application.

Without authentication,

anyone could check your account balance or transfer money.

To prevent unauthorized access,

APIs use authentication.

Authentication verifies the identity of the client before allowing access.

Some common authentication methods are:

---

### API Key

An API Key is a unique key provided by the API provider.

The client includes this key with every request.

Example:

```text
x-api-key: abc123xyz456
```

The server checks whether the API Key is valid before processing the request.

API Keys are commonly used for public APIs like:

- Weather APIs
- Google Maps API
- OpenAI API

---

### JWT (JSON Web Token)

JWT is one of the most popular authentication methods used today.

After a user logs in successfully,

the server generates a token.

The client stores this token and sends it with future requests.

Example:

```text
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

The server verifies the token before returning any protected data.

Many modern web and mobile applications use JWT authentication.

---

### OAuth

OAuth allows users to log in using another service without sharing their password.

Examples:

- Continue with Google
- Continue with GitHub
- Continue with Facebook

Instead of giving your password to every application,

OAuth securely authorizes access through a trusted provider.

> 📘 We'll learn API Authentication in much more detail in a dedicated chapter.

---

## 16. Advantages of APIs

APIs provide many benefits for both developers and businesses.

### Reusability

The same API can be used by:

- Web Applications
- Mobile Applications
- Desktop Applications

without rewriting the business logic.

---

### Security

Clients never communicate directly with the database.

The API controls:

- Authentication
- Authorization
- Data Validation

This makes applications much safer.

---

### Scalability

Applications can be divided into smaller APIs.

Each API can be developed,

updated,

and scaled independently.

---

### Easy Integration

Different applications can communicate easily.

For example,

a shopping website can integrate:

- Google Maps API
- Razorpay API
- Email API

without building everything from scratch.

---

### Faster Development

Developers can reuse existing APIs instead of rebuilding the same functionality.

This reduces development time.

---

## 17. Limitations of APIs

Although APIs are very useful,

they also have some limitations.

### Network Dependency

Most APIs require an internet connection.

If the network is unavailable,

the API cannot be accessed.

---

### Latency

Every API request travels through the network.

This introduces some delay before the response reaches the client.

---

### Rate Limits

Many public APIs limit how many requests a client can make.

If the limit is exceeded,

the API may temporarily reject further requests.

---

### Authentication Requirements

Many APIs require:

- API Keys
- JWT Tokens
- OAuth

Without proper authentication,

the API cannot be accessed.

---

### Downtime

If an API server becomes unavailable,

applications depending on that API may stop working until the service is restored.

---

> [!TIP]
> **💡 Did You Know?**
>
> When you scroll through Instagram, your phone isn't downloading the entire application again.
>
> Instead, it continuously calls different APIs such as:
> - Feed API
> - Stories API
> - Comments API
> - Notifications API
> - Search API
>
> Each API returns only the data needed for that specific feature.
>
> This is one reason why modern applications feel fast and responsive.

---

## 18. Common Interview Questions

### Q1. What is an API?

An API (Application Programming Interface) is a set of rules that allows different software applications to communicate with each other.

---

### Q2. Why do we need APIs?

APIs provide a secure and organized way for applications to exchange data and functionality without exposing internal implementation details.

---

### Q3. How does an API work?

The client sends a request to the API.

The API processes the request,

interacts with business logic and databases,

and returns a structured response to the client.

---

### Q4. What is the difference between an API and a Database?

A database stores data.

An API provides controlled access to that data.

Clients should communicate with the API instead of accessing the database directly.

---

### Q5. What are some common API response formats?

The two most common formats are:

- JSON
- XML

JSON is the most widely used today.

---

### Q6. What are the different types of APIs?

- Public APIs
- Private APIs
- Partner APIs
- Library APIs

---

### Q7. What is API Authentication?

API Authentication verifies the identity of the client before allowing access to protected resources.

---

### Q8. Name some common API authentication methods.

- API Key
- JWT
- OAuth

---

### Q9. Can one application use multiple APIs?

Yes.

Most modern applications use many APIs working together.

For example,

Uber uses:

- Authentication API
- Maps API
- Payment API
- Ride Matching API
- Notification API

---

### Q10. Give some real-world examples of APIs.

Examples include:

- Google Maps API
- OpenAI API
- GitHub API
- Stripe API
- Razorpay API
- Twilio API

---

## 19. Summary

An API (Application Programming Interface) provides a standardized way for software applications to communicate with each other.

Instead of directly accessing databases or internal business logic,

clients send requests to APIs,

which process the request,

perform the required operations,

and return structured responses.

Modern applications rely on many APIs working together to provide secure,

scalable,

and efficient services.

Understanding APIs is essential because they form the foundation of communication between modern software systems.

---

## ✅ Key Takeaway

- APIs allow different applications to communicate.
- Clients interact with APIs instead of directly accessing databases.
- APIs define clear inputs and predictable outputs.
- Most modern APIs exchange data using JSON.
- Modern applications are built using multiple APIs working together.

---

## 🚀 What's Next?

Now we understand what an API is and how applications communicate using APIs.

However,

not all APIs are designed in the same way.

One of the most popular API architectures used today is **REST (Representational State Transfer).**

In the next chapter,

we'll learn what REST APIs are,

their design principles,

how they use HTTP methods,

and why they have become the standard choice for modern web development.

---
## Reference Images
![Image 1](images/api_image1.png)
![Image 2](images/api_image2.png)
![Image 3](images/api_image3.png)
![Image 4](images/api_image4.png)
![Image 5](images/api_image5.png)
