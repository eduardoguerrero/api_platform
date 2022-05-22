# API Platform Tutorial

Well hi there! This repository holds the code and script
for the [API Platform](https://symfonycasts.com/screencast/api-platform) course on SymfonyCasts.

## Setup

If you've just downloaded the code, congratulations!!

To get it working, follow these steps:

**Download Composer dependencies**

Make sure you have [Composer installed](https://getcomposer.org/download/)
and then run:

```
composer install
```

You may alternatively need to run `php composer.phar install`, depending
on how you installed Composer.

**Start the built-in web server**

You can use Nginx or Apache, but Symfony's local web server
works even better.

To install the Symfony local web server, follow
"Downloading the Symfony client" instructions found
here: https://symfony.com/download - you only need to do this
once on your system.

Then, to start the web server, open a terminal, move into the
project, and run:

```
symfony serve
```

(If this is your first time using this command, you may see an
error that you need to run `symfony server:ca:install` first).

Now check out the site at `https://localhost:8000`

Have fun!

## Have Ideas, Feedback or an Issue?

If you have suggestions or questions, please feel free to
open an issue on this repository or comment on the course
itself. We're watching both :).

## Thanks!

And as always, thanks so much for your support and letting
us do what we love!

<3 Your friends at SymfonyCasts


## Useful commands

```bash
symfony serve -d

composer require api

composer require maker:1.11 --dev

php bin/console make:entity

composer require migrations:2.0.0 -W

php /bin/console doctrine:database:create

php bin/console make:migration

php bin/console doctrine:migrations:migrate

php /bin/console debug:router

composer require nesbot/carbon

php bin/console debug:config api_platform

symfony server:stop

http://localhost:8000/api/cheeses/1.csv

http://localhost:000/api/cheeses.csv

php bin/console make:entity

php bin/console doctrine:schema:drop --full-database --force
```

### Creates a cheeses resource.

Use IRI (Internationalized Resource Identifier) instead ID and have a look to the owner value.

/api/cheeses POST
```
{
    "title": "This is a new chees",
    "price": 1000,
    "owner": "/api/users/1",
    "description": "This is short description"
}
```

### Creates a user resource

API platform will create the relation between user and cheese

POST /api/users

```
{
"email": "escobarguerrer@gmail.com",
"password": "xxxxx",
"username": "rene.escobar",
"cheeseListings":[
   {
      "title": "blue cheese",
      "price": 2000,
      "description":"short description"
   } 
  ]
}
```

### Replaces the user resource

PUT /api/users/{id}

```
{
    "cheeseListings": [    
      "api/cheeses/1",
      "api/cheeses/2"    
   ]
}
```

### Retrieves a User resource

GET /api/users/{id}

http://127.0.0.1:8000/api/users/2.json

```
{
  email: "escobarguerrero2@gmail.com",
  username: "rene.escobar03",
  cheeseListings: [
    {
      title: "This is a new chees",
      price: 1000,
    },
    {
      title: "Hmm new cheese",
      price: 1000,
    },
  ],
}
```

### Retrieve just username

http://127.0.0.1:8000/api/users/2.json?properties[]=username

```
{
  username: "rene.escobar03"
}
```


### Retrieve just username and title

http://127.0.0.1:8000/api/users/2.json?properties[]=username&properties[cheeseListings][]=title

```
{
  username: "rene.escobar03",
  cheeseListings: [
    {
      title: "This is a new chees"
    },
    {
      title: "Hmm new cheese"
    },
  ],
}
```

### Retrieves the collection of cheeses resources

GET /api/users/{id}/cheese_listings

```
[
  {
    "title": "This is a new chees",
    "description": "This is short description",
    "price": 1000,
    "owner": "/api/users/2",
    "shortDescription": "This is short description",
    "createdAtAgo": "2 days ago"
  },
  {
    "title": "Hmm new cheese",
    "description": "Short description",
    "price": 1000,
    "owner": "/api/users/2",
    "shortDescription": "Short description",
    "createdAtAgo": "2 days ago"
  }
]
```

### API docs

http://127.0.0.1:8000/api/docs

![Alt text](example.png?raw=true "Api docs")
