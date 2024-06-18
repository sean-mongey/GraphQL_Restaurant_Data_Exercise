# GraphQL Restaurant API

This project is a GraphQL API for managing restaurant data, created as a learning exercise from the "MIT xPro: Professional Certificate in Coding: Full Stack Development with MERN" course. 

## Author

**Sean Mongey**

## Description

This API allows users to query and manage a list of restaurants and their dishes. It supports operations such as fetching restaurant details, adding a new restaurant, deleting a restaurant, and editing restaurant information.

## Prerequisites

Before you begin, ensure you have met the following requirements:

- **Node.js**: You should have Node.js installed on your machine. You can download it from [Node.js official website](https://nodejs.org/).
- **NPM**: Node Package Manager, which is included with Node.js.
- **Git**: For cloning the repository. You can download it from [Git official website](https://git-scm.com/).

## Installation

1. **Clone the Repository**

    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```

2. **Install Dependencies**

    Run the following command to install the required npm packages:

    ```bash
    npm install
    ```

## Usage

1. **Run the Application**

    Start the server by running:

    ```bash
    node index.js
    ```

    The server will start and listen on port 5500. You should see the following message:

    ```
    Running Graphql on Port: 5500
    ```

2. **Access GraphiQL**

    Open your browser and go to:

    ```
    http://localhost:5500/graphql
    ```

    This will open the GraphiQL interface, where you can interact with the API.

## GraphQL Schema

The API provides the following types and operations:

### Types

- **Query**

    ```graphql
    type Query {
        restaurant(id: Int): restaurant
        restaurants: [restaurant]
    }
    ```

- **restaurant**

    ```graphql
    type restaurant {
        id: Int
        name: String
        description: String
        dishes: [Dish]
    }
    ```

- **Dish**

    ```graphql
    type Dish {
        name: String
        price: Int
    }
    ```

- **restaurantInput**

    ```graphql
    input restaurantInput {
        name: String
        description: String
    }
    ```

- **DeleteResponse**

    ```graphql
    type DeleteResponse {
        ok: Boolean!
    }
    ```

- **Mutation**

    ```graphql
    type Mutation {
        setrestaurant(input: restaurantInput): restaurant
        deleterestaurant(id: Int!): DeleteResponse
        editrestaurant(id: Int!, name: String!): restaurant
    }
    ```

### Example Queries and Mutations

- **Fetch All Restaurants**

    ```graphql
    query {
        restaurants {
            id
            name
            description
            dishes {
                name
                price
            }
        }
    }
    ```

- **Fetch a Single Restaurant by ID**

    ```graphql
    query {
        restaurant(id: 1) {
            id
            name
            description
            dishes {
                name
                price
            }
        }
    }
    ```

- **Add a New Restaurant**

    ```graphql
    mutation {
        setrestaurant(input: { name: "New Restaurant", description: "A new place to eat" }) {
            id
            name
            description
        }
    }
    ```

- **Delete a Restaurant**

    ```graphql
    mutation {
        deleterestaurant(id: 1) {
            ok
        }
    }
    ```

- **Edit a Restaurant's Name**

    ```graphql
    mutation {
        editrestaurant(id: 1, name: "Updated Name") {
            id
            name
            description
        }
    }
    ```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
