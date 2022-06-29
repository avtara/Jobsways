# Users

**POST /users**
----
  Creates a new User and returns the new object.
* **URL Params**  
  None
* **Headers**  
  Content-Type: application/json  
* **Data Params**  
```
  {
    name: string,
    password: string,
    is_admin: boolean,
    email: string
  }
```
* **Success Response:**  
  * **Code:** 200  
  **Body Response:** 
```
{
  id: integer
  name: string,
  is_admin: boolean,
  email: string
  created_at: datetime(iso 8601)
  updated_at: datetime(iso 8601)
}
```

**GET /users/:id**
----
  Returns the specified user.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`  
* **Success Response:**  
  * **Code:** 200  
  **Body Response:**   
```
{
  id: integer
  name: string,
  is_admin: boolean,
  email: string
  created_at: datetime(iso 8601)
  updated_at: datetime(iso 8601)
}
```
* **Error Response:**  
  * **Code:** 403  
  **Body Response:** `{ error : "Forbidden access" }`  
  OR  
  * **Code:** 401  
  **Body Response:** `{ error : error : "You are unauthorized to make this request." }`

**GET /users/:id/applied**
----
  Returns all Orders associated with the specified user.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`
* **Success Response:**  
  * **Code:** 200  
  **Body Response:**  
```
{
    applications: [
        {
            id: integer,
            company : {
                name: string,    
            },
            jobs: {
                name: string,
                role: string,
                type: string,
            }
            status: string,
            created_at: datetime(iso 8601)
        }    
    ]
}
```
* **Error Response:**  
  * **Code:** 403  
  **Body Response:** `{ error : "Forbidden access" }`  
  OR  
  * **Code:** 401  
  **Body Response:** `{ error : error : "You are unauthorized to make this request." }`


**POST /users/session**
----
  Make token to use secure resource.
* **URL Params**  
  None
* **Headers**  
  Content-Type: application/json  
* **Data Params**
```
  {
    email: string,
    password: string
  }
```
* **Success Response:**  
  * **Code:** 200  
  **Body Response:**  
```
  {
    token: string
  }
```
* **Error Response:**  
  * **Code:** 403  
  **Body Response:** `{ error : "Email or password is not correct" }`  

# Jobs
**GET /jobs**
----
  Returns all products in the system.
* **URL Params**  
  None
* **Data Params**  
  None
* **Query Params**  
  *Optional:* `name=[string]`  
  *Optional:* `type=[string]`  
  *Optional:* `role=[string]`  
  *Optional:* `experience=[int]`
* **Headers**  
  Content-Type: application/json  
* **Success Response:** 
* **Code:** 200  
  **Body Response:**  
```
{
  jobs: 
    [
        {
            name: string,
            role: string,
            type: string,
            experience: int,
            company: {
                name: string,
                location: string,
            },
            created_at: datetime(iso 8601)
        }
    ]
}
```
* **Error Response:**  
  * **Code:** 404  
  **Body Response:** `{ error : "Jobs doesn't exist" }`  

**GET /jobs/:id**
----
  Returns spesific jobs in the system.
* **URL Params**  
  *Required:* `id=[integer]`  
* **Data Params**  
  None
* **Query Params**  
  None
* **Headers**  
  Content-Type: application/json  
* **Success Response:** 
* **Code:** 200  
  **Body Response:**  
```
{
  jobs: 
    [
        {
            name: string,
            role: string,
            type: string,
            experience: int,
            description: string
            company: {
                name: string,
                location: string,
                total_employee: integer,
                email: string
            },
            created_at: datetime(iso 8601)
            updated_at: datetime(iso 8601)
        }
    ]
}
```
* **Error Response:**  
  * **Code:** 404  
  **Body Response:** `{ error : "Job doesn't exist" }`  


<!-- Example -->
<!-- **PATCH /orders/:id**
----
  Updates fields on the specified order and returns the updated object.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
```
  {
  	product: <product_id>,
  	quantity: integer 
  }
```
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`
* **Success Response:**  
* **Code:** 200  
  **Body Response:**  `{ <order_object> }` 
* **Error Response:**  
  * **Code:** 404  
  **Body Response:** `{ error : "Order doesn't exist" }`  
  OR  
  * **Code:** 401  
  **Body Response:** `{ error : error : "You are unauthorized to make this request." }`

**DELETE /orders/:id**
----
  Deletes the specified order.
* **URL Params**  
  *Required:* `id=[integer]`
* **Data Params**  
  None
* **Headers**  
  Content-Type: application/json  
  Authorization: Bearer `<OAuth Token>`
* **Success Response:** 
  * **Code:** 204 
* **Error Response:**  
  * **Code:** 404  
  **Body Response:** `{ error : "Order doesn't exist" }`  
  OR  
  * **Code:** 401  
  **Body Response:** `{ error : error : "You are unauthorized to make this request." }` -->