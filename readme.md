# json server

## History

goals: building fake api for frontend/database prototyping.

## What is json server?

a fake rest apis with zero coding for prototyping backend/database.

## Json server use cases

- easily prototype data
- mocked data can be used quickly in order to prototype frontend components
- data should be fetched asynchronously
- not time-cunsuming like node + express + mangodb
- simple json/js file as a database
- query a list of items
- query by id
- query by operators
- query parent/child entities
- filtering, sorting, pagination and searching
- make get, post, put, patch, delete reqs

## Prerequsits

- json data format (example: products(id, title, category, price, description) - reviews (id, rating, comment, productId))
- basic knowledge about rest-api

## Scripts to up and running json server

- basic
    json-server --watch db.json
    json-server --watch data/db.json
    json-server --watch data.js (commonjs syntax)
- advance
    json-server --watch db.json --port 4000

    routes.json > { "/api/v1/*": "/$1", "/products/:category": "/products?category=:category" }
    json-server --watch db.json --port 4000 --routes routes.json

## Default server addresses

localhost:3000
localhost:3000/products
localhost:3000/reviews

## Filtering

localhost:3000/products?category=electrinics
localhost:3000/products?category=electrinics&discount.type=birthdate

### Operators

localhost:3000/products?price_gte=2000&price_lte=6000
localhost:3000/products?id_ne=1
localhost:3000/products?category_like=^f

## Slice

localhost:3000/products?_start=5&_end=10

## Sorting

localhost:3000/products?_sort=price
localhost:3000/products?_sort=price&_order=desc
localhost:3000/products?_sort=price,category&_order=desc,asc

## Pagination

localhost:3000/products?_page=1
localhost:3000/products?_page=1&_limit=2

Note: default value for _limit is 10.

## Searhing

localhost:3000/products?q=xbox

## Ralationships

localhost:3000/products?_embed=reviews
localhost:3000/products/1?_embed=reviews
localhost:3000/reviews?_expand=product

## HTTP requests

postman - insomnia - thunder client

### POST request

url: localhost:3000/products
body: { ... }

### PUT request

url: localhost:3000/products/11
body: { ... }

### PATCH request

url: localhost:3000/products/11
body: { "price": 8000 }

### DELETE request

url: localhost:3000/products/11
