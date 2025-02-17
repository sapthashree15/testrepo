```markdown
# Hands-on Lab - CRUD Operations with JavaScript

![Cognitive Class Logo](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-CD0210EN-SkillsNetwork/images/IDSN-logo.png)

## Estimated Time Needed: 60 mins

In this lab, you will learn how to create a **Products' list** using an Express.js server. Your application should allow you to add a product, retrieve the products, retrieve a specific product with its id, update a specific product with its id, and delete a product with its id. All these operations will be achieved through the REST API endpoints in your Express.js server.

You will create an application with API endpoints to perform Create, Retrieve, Update, and Delete operations on the above data using Express.js.

You will use cURL and POSTMAN to test the implemented endpoints.

## Objectives:

After completing this lab you will be able to:

- Create API endpoints to perform Create, Retrieve, Update, and Delete operations on transient data with an Express.js server.
- Create REST API endpoints, and use POSTMAN to test your REST APIs.

## Set-up: Create Application

1. Open a terminal window by using the menu in the editor: **Terminal > New Terminal**.

2. Change to your project folder, if you are not in the project folder already.

   ```sh
   cd /home/project
   ```

3. Run the following command to create a new directory for your project.

   ```sh
   mkdir products-api
   cd products-api
   ```

4. Initialize a new Node.js project.

   ```sh
   npm init -y
   ```

5. Install Express and other required packages.

   ```sh
   npm install express body-parser cors
   ```

6. Create a new file named `server.js`.

   ```sh
   touch server.js
   ```
::page{title="Exercise 1: Understand the server application"}

1. In the Files Explorer open the **products-api** folder and view **server.js**.

2. You first need to import the packages required to create REST APIs with Express.

```javascript
const express = require('express');
const bodyParser = require('body-parser');
const cors = require('cors');
```

3. You can then create the Express application, which will service all the REST APIs for adding, retrieving, updating, and deleting products.

```javascript
const app = express();
const port = 5000;

// Middleware
app.use(cors());
app.use(bodyParser.json());
```

4. The code has precreated products added to the list. These are defined in the following code.

```javascript
let products = [
    { id: 143, name: 'Notebook', price: 5.49 },
    { id: 144, name: 'Black Marker', price: 1.99 }
];
```

5. Now that the server is defined, you will create the REST API endpoints and define the routes or paths, one for each of the following operations.
- Retrieve all the products - `GET` Request Method
- Retrieve a product by its id - `GET` Request Method
- Add a product - `POST` Request Method
- Update a product by its id - `PUT` Request Method
- Delete a product by its id - `DELETE` Request Method

Add the following code to **server.js** in the space provided.

```javascript
// Example request - http://localhost:5000/products
app.get('/products', (req, res) => {
    res.json(products);
});

// Example request - http://localhost:5000/products/144 - with method GET
app.get('/products/:id', (req, res) => {
    const id = parseInt(req.params.id);
    const product = products.find(x => x.id === id);
    if (product) {
        res.json(product);
    } else {
        res.status(404).json({ message: 'Product not found' });
    }
});

// Example request - http://localhost:5000/products - with method POST
app.post('/products', (req, res) => {
    const newProduct = req.body;
    products.push(newProduct);
    res.status(201).send(); // Return a 201 status with no content
});

// Example request - http://localhost:5000/products/144 - with method PUT
app.put('/products/:id', (req, res) => {
    const id = parseInt(req.params.id);
    const updatedProduct = req.body;
    const product = products.find(x => x.id === id);
    if (product) {
        Object.assign(product, updatedProduct); // Update product properties
        res.status(204).send(); // Return a 204 status with no content
    } else {
        res.status(404).json({ message: 'Product not found' });
    }
});

// Example request - http://localhost:5000/products/144 - with method DELETE
app.delete('/products/:id', (req, res) => {
    const id = parseInt(req.params.id);
    const productIndex = products.findIndex(x => x.id === id);
    if (productIndex !== -1) {
        products.splice(productIndex, 1); // Remove product from array
        res.status(204).send(); // Return a 204 status with no content
    } else {
        res.status(404).json({ message: 'Product not found' });
    }
});
```

## Run and Test the Server with cURL

1. In the terminal, run the Node.js server using the following command.

   ```bash
   node server.js
   ```

   The server starts running and listening at port 5000.

2. Open another terminal by clicking the Terminal menu and selecting **New Terminal**.

3. In the new terminal, run the following command to access the **http://localhost:5000/products** API endpoint. The `curl` command stands for `Client URL` and is used for command line interfacing with the server serving REST API endpoints. It is, by default, a `GET` request.

   ```bash
   curl http://localhost:5000/products
   ```

   This returns a JSON with the products that have been preloaded.

4. In the terminal, run the following command to add a product to the list. This will be a POST request to which you will pass the product parameter as a JSON.

   ```bash
   curl -X POST -H "Content-Type: application/json" \
       -d '{"id": 145, "name": "Pen", "price": 2.5}' \
       http://localhost:5000/products
   ```

   This command will not return any output. It will add the product to the list of products.

5. Verify if the product is added by running the following command.

   ```bash
   curl http://localhost:5000/products/145
   ```

   This should return the details of the product you just added with a POST request.

## Using POSTMAN to Test the REST API Endpoints

While the `GET` endpoints are easy to test with `curl` using a command line interface, the `POST`, `PUT`, and `DELETE` commands can be cumbersome. To circumvent this problem, you can use Postman, which is a software that is available as a service.

1. Go to [Postman](https://www.postman.com/) and sign up for an account.

2. Click **Create New** to start creating a request to the REST API endpoint.

3. Choose **HTTP Request** from the options that you are presented with.

4. Paste the URL `http://localhost:5000/products` into the address bar. Change the request type to `POST`. To send input as JSON, choose `raw` -> `body` -> `JSON`.

5. Enter the following JSON object and click the `Send` button. This will add the product to your previous list of products.

   ```json
   {
       "id":146,
       "name":"Laptop Bag",
       "price":45.00
   }
   ```

6. Verify the list of products to ensure that the request has gone through and the product is added. Change the request type to `GET` and remove the JSON object from the request body. Click `Send` and observe the output in the response window.

7. Test the `PUT` endpoint to update product details by changing the price of the item with id 146 to 42.00. Set the request type to `PUT` and add the product id to the end of the URL and add the value to be changed as a JSON body and click `Send`.

   ```json
   {
       "price":42.00
   }
   ```

8. Verify the product with id 146 to ensure that the request has gone through and the product is updated. Change the request type to `GET` and remove the JSON object from the request body. Click `Send` and observe the output in the response window.

## Practice Labs

1. Update product details of the product with id 144 by changing its price to 2.50.

   ```json
   {
       "price":2.50
   }
   ```

2. Add the following product using the `POST` method.

   ```json
   {
       "id":142,
       "name":"Eraser",
       "price":1.50
   }
   ```

3. Delete the product with id 142.

## Congratulations! You have completed the lab for CRUD operations with JavaScript.

### Summary:

In this lab, you have performed CRUD Operations like GET, POST, PUT, and DELETE on a JavaScript server app using Express.js and tested the above methods using POSTMAN.
