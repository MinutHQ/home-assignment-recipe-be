# Minut home assignment - Recipe backend

A small toy backend built for browsing, adding & removing recipes. Intended for
use in home assignments. Recipes are stored in a simple local json database.

## Prerequisites

Make sure you have [nodejs][] and [npm][] installed.

[npm]: https://www.npmjs.com/
[nodejs]: https://nodejs.org/en/

## Getting started

Install dependencies:

```
npm install
```

Start the backend:

```
npm start
```

The backend will be serving requests from [localhost][], port 3000. You can
visit [this link][getrecipes] in your browser to verify that it is up and
running correctly.

When building a mobile app client, the backend url will be the IP address
of the hosting computer. When the phone is connected to the same network,
the backend url will be `http://xxx.xxx.xxx.xxx:3000`.

[localhost]: http://localhost:3000
[getrecipes]: http://localhost:3000/recipes

## Endpoints

These are the available endpoints

1. `GET /recipes`
   - Returns the list of stored recipes
2. `POST /recipes`
   - Store a recipe in the backend
3. `GET /recipes/:id`
   - Retrieve a specific recipe
4. `PUT /recipes/:id`
   - Update a specific recipe
5. `DELETE /recipes/:id`
   - Delete a recipe
6. `GET /reset`
   - Development endpoint to reset the database to its original state

You can find them defined in `endpoints.js`.

## Recipe

This is the shape of a recipe:

```typescript
interface Recipe {
  title: string; // recipe title; REQUIRED
  description: string; // short description of the recipe; REQUIRED
  ingredients: string[]; // an array of strings for listing ingredients; REQUIRED
  instructions: string; // instructions on how to prepare the food; REQUIRED
  imageUrl?: string; // an URL to an image for the recipe; OPTIONAL
  sourceUrl?: string; // an URL to the original recipe; OPTIONAL
}
```

When creating new recipes by sending POST or PUT requests, the request body will be
validated according to this model.

Sample recipes and and the schema validator can be found in `recipes.js`.

## Database

The recipes are stored locally in `recipe-db.json`. If you want to reset the
database to its original state use the `reset` endpoint above or visit
[this link](http://localhost:3000/reset) when the backend is running.
