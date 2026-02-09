# Understanding APIs

This short document introduces the concept of APIs (application programming interfaces). This is really a fundamental component of modern software and the world we live in! Let's start with a useful video that explains the concept well:

https://user-images.githubusercontent.com/48418248/206932791-884abc1d-86f6-4b79-ba70-c0dd00e34417.mp4"

Therefore, think of an API as a **waiter in a restaurant**:
- You (client) make a **request** ("I'd like the pasta")
- The waiter takes it to the kitchen (server)
- The kitchen prepares your order
- The waiter brings back a **response** (your pasta)

## REST APIs

Many (most?) APIs are built using [RESTful](https://restfulapi.net/) protocols. REST (standing for REpresentional State Transfer) is a set of guidelines to standardise communications between these applications/services. Although we don't need to go through everything here its worth touching on some fundamentals. Some initial terminology of the key elements of an API interaction:

- __The client__: The program that is connecting to the API. This is the app/service that is requesting information or requesting information be added.
- __The request__: What __the client__ is requesting from the API.   
- __The resource__: The information or object __the client__ is requesting. This could be flight availability (as in the video) or a photo from Facebook, or pretty much anything that may be served over the internet.
- __The server__: The place where __the resource__ lives (e.g. the database we want to query or update).
- __The response__: What __the server__ sends back over the API in response to __the request__ made by the __client__ (e.g. __the resource__).


REST APIs use **HTTP** (the same protocol your web browser uses) to transfer data.

#### Key Components:

1. **URL (Endpoint)** - The address where you send your request
   - Example: `https://api.example.com/data`

2. **HTTP Method** - What action you want to perform
   - `GET`: Retrieve data (most common for ingestion)
   - `POST`: Send new data
   - `PUT`: Update existing data
   - `DELETE`: Remove data

3. **Headers** - Additional information about the request
   - Authentication keys
   - Content type (JSON, XML, etc.)

4. **Response** - Data sent back by the server
   - Usually in **JSON** format
   - Includes a **status code** (200 = success, 404 = not found, etc.)

For example, __the client__ may ask __the server__ to __GET__ the flight price of a given flight. After this __the client__ may request __the server__ to __POST__ a new customer booking record into their system (i.e. buy a flight ticket). We could also imagine future events such as updating the passenger name (a __PUT__ request) or cancelling the booking (a __DELETE__ request). Note these would all be separate requests ... each request will use only one HTTP method.

The actual client request may look something like this:

```http
GET https://api.fakesite.com/v1?id=1234
```

Here we are making a __GET__ request to the API URL querying for an item with the ID 1234. The full URL is known as the endpoint of the request.

The response we receive may look something like this:

#### Common Response Formats:

**JSON** (JavaScript Object Notation) - Most common
```json
{
  'status_code': 200,
  'id': 1234,
  'content': 'blah, blah, blah'
}
```
The result includes the requested ID and the requested resource ("content"). We also get a "status_code" of 200 - which means "OK" (i.e. the request was successful). Some other common codes are listed [here](https://restfulapi.net/http-status-codes/).

This gives a basic overview - although obviously there is much further we can (and will) go with this. In the next workbook, we will actually extract data through API or make an API!


Other examples:

```json
{
  "temperature": 25.5,
  "sensor_id": "sensor-001",
  "timestamp": "2024-02-08T10:30:00"
}
```

It can also be a **CSV** (Comma-Separated Values)
```
temperature,sensor_id,timestamp
25.5,sensor-001,2024-02-08T10:30:00
```
