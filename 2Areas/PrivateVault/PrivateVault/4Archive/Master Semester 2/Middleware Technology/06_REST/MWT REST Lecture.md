[[5_REST_v1.0.0.pdf]]
# General 
- **Re**presentational **S**tate **T**ransfer
- Architectural style of design pattern for APIs
- A communication protocol 

The motivation of REST was to capture characteristics of the Web which made the web successful.
- URL Addressable resources 
- HTTP Resources 
- Request - Response - Display Response

# Nouns (Resources)
- Key abstraction of information
- Represents a **global identifier**
- Conceptual mapping to a set of entities
- REST uses **URI** to identify resources 

# Verbs  
You can take actions on the noun. (CRUD basically?)

*You should learn them by heart*
- Safe method may be cached 
- Idempotent method may be retried

### Idempotence and safety
*Idempotent*
Will produce the same results when executed one or multiple results.

*Safe* 
- Operations that do not modify the state on the server side at all. 
- read-only, zero side-effects


| Verb    | Idempotent | Safe |
| ------- | ---------- | ---- |
| OPTIONS | yes        | yes  |
| **GET**     | yes        | yes  |
| HEAD    | yes        | yes  |
| **PUT**     | yes        | no   |
| **POST**    | no         | no   |
| **DELETE**  | yes        | no   |
| PATCH   | no         | no   |

*PATCH* is used for partial updates to resources. 

# Presentations
Rest APIs can return the resource representations in  different formats. 
Usually JSON. 

# Principles 
*Stateless:* The request will contain all the required information to make the server understand the request.

*Client-Server:* architecture enables a **uniform interface** and **separate clients**

*Uniform Interface:* 
- Resource identification 
- Resource Manipulation using representations 
- Self-descriptive messages

*Cacheable:* 
- Better performance 
- The client cache can reuse the response for equivalent responses in the future 

*Layered system*
- Stability by limiting component behavior as each layer cannot interact beyond the next immediate layer they are in 

*Code on demand*
- Optional 
- Permits client's code or applets to be downloaded and to be used within the app.


# CRUD
- Create -> POST 
- Read -> GET
- Update -> PUT 
- Delete -> DELETE

# Richardson Maturity Model
Level 0: RPC (Remote Procedure Call) 
Level 1: Resources 
Level 2: HTTP Verbs
Level 3: Hypermedia 

## Objectives
The student understands the concepts of an API and synchronous communication in distributed systems and can explain it in own words.

### Review questions
- **Identify good and bad API examples and explain why**
- Describe the concepts of Verbs and Nouns
- When is an invocation idempotent and safe? What does it mean? Provide examples
- Describe in your own words the mapping of REST calls to database (SQL) and CRUD calls
