<!-- what is  graphQL? -->

GraphQl is a query langugae for APIs and a runtime to execute those queries. It allow clients to request only the date, they needed, making it more efficient than traditional REST APIs. It provides a flexible and organized way to interact with your data, using a single endpoint for all request.

<!-- Real-World Example: Online Shopping App -->

The Problem with REST APIs:
Imagine an e-commerce app where you want to display:

Product details: Name, price, description.
Reviews: User names, ratings, comments.
In a REST API:

You’d likely have to make multiple requests:
/products/:id to fetch product details.
/products/:id/reviews to fetch reviews.
These endpoints may return too much or too little data, requiring you to filter or combine responses manually.

<!-- Basic Types and Queries -->

    <!-- GraphQL Type -->

1.  scalar types
    INT, float, string, boolean, ID

2.  Object Types

type Product {
id: ID
name: String
price: Float
inStock: Boolean
} 3. Input Types :Input Types: Used for passing structured objects into queries or mutations.

input ProductInput {
name:String,
price:Float
}

   <!-- Defining a query -->

type Query{
getProduct(id:ID):Product
allProduct:[Product]
}
tyoe Product {
id:ID
name:string
price:Float
inStock:Boolean
}

A client can request data using Quries

query{
getProduct(id:"123"){
name
price
inStock
}
}

Modules-3:<!--How to build a graphQL API with Nodejs  -->

step -1: make a apollo server and pas tyepdef and resolver as argument
step -2: typedef define the schema of your graphQL API. They describe the data types, relationships, and operations(queries, mutations, subscription) that are available.

<!--

type Product {
  id: ID!
  name: String!
  price: Float!
  inStock: Boolean!
}

type Query {
  getProduct(id: ID!): Product
  allProducts: [Product]
}

type Mutation {
  addProduct(name: String!, price: Float!, inStock: Boolean!): Product
}

 -->

<!-- 2. Resolver: -->

resolver are function that implement the logic for each field define in the typeDef. They specify how to fetch or modify the data when a query or mutation is executed.

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

 <!-- Modules-4: Mutation -->

A mutation is like making a request to change or add Data in the database. You use mutation to create, update, or delete data. For example, in the same shop, you might want to "add new product"

Analogy: Now , you decide to order a pizza. You call a shop and request them to make a pizza for you.
here, You are modifying the system(adding an order) rather than just asking for information.

<!--
 mutation {
   type User{
   id:ID,
   ...
   }
   input CreateUserInput{
              id:ID,
              name:String
        }
   createUser(input:CreateUserInput):User
  }
 -->

<!-- 5 -->
<!-- 6 -->

Module-7<!--GraphQl in react and use mutation hook  -->

Module-8 <!--: Context,Fragments,Union Result Boxes -->

user:(parent,args,contet,info)=>{

}
parent: when you access parent in reslover function then it return previous level of graphql result.

query-> user -> favoriteMovies

analogy: for user , we also need to find the favorite movie. right !

<!--
type-def.js-

type User{
    id:ID!
    name: String!
    username:String!
    age:Int!
    nationality: String!
    friends:[User!]
    favoriteMovies:[Movie]
 }

 type Query{
     users:[User!]!
}


resolver.js-

   Query{
     user:()=>{
        return  UserList;
     }
   }

   User:{
     favoriteMovies:(parent)=>{
           // here we get value retur by user(means the value return by higher level)
           console.log(parent);
                        return _.filter(MovieList,(movie)=>movie.yearOfPublication<= 2010)

        }


   }



 -->

context:-

Fragement: wo what a fragment?
