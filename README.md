# Documentation

## Introduction
Welcome to the singerapi, the [I-Am-a-Singer](https://en.wikipedia.org/wiki/I_Am_a_Singer_(Chinese_TV_series)) API! This documentation should help you familiarise yourself with the resources available and how to consume them with HTTP requests. If you're after a native helper library then I suggest you scroll down and check out what's available. Read through the getting started section before you dive in. Most of your problems should be solved just by reading through it.

## Getting started

> TODO: complete it

Let's make our first API request to the I-AM-A-SINGER API!

Open up a terminal and use curl or httpie to make an API request for a resource. In the example below, we're trying to get the first planet, Tatooine:

http://127.0.0.1/singerapi/api/
We'll use httpie for our examples as it displays responses nicely and gives us a whole lot more useful information. If you don't want to download httpie, just use the curl command instead.

Here is the response we get:

HTTP/1.0 200 OK
Content-Type: application/json
{
}
If your response looks slightly different don't panic. This is probably because more data has been added to swapi since we made this documentation.

## Base URL
The Base URL is the root URL for all of the API, if you ever make a request to swapi and you get back a 404 NOT FOUND response then check the Base URL first.

The Base URL for swapi is:

https://127.0.0.1/singerapi/api
The documentation below assumes you are prepending the Base URL to the endpoints in order to make requests.

## Rate limiting
Swapi has rate limiting to prevent malicious abuse (as if anyone would abuse Star Wars data!) and to make sure our service can handle a potentially large amount of traffic. Rate limiting is done via IP address and is currently limited to 10,000 API request per day. This is enough to request all the data on the website at least ten times over. There should be no reason for hitting the rate limit.

## Authentication
Swapi is a completely open API. No authentication is required to query and get data. This also means that we've limited what you can do to just GET-ing the data. If you find a mistake in the data, then tweet the author or email him.

JSON Schema
All resources support JSON Schema. Making a request to /api/<resource>/schema will give you the details of that resource. This will allow you to programmatically inspect the attributes of that resource and their types.

## Searching
All resources support a search parameter that filters the set of resources returned. This allows you to make queries like:

https://swapi.co/api/people/?search=r2

All searches will use case-insensitive partial matches on the set of search fields. To see the set of search fields for each resource, check out the individual resource documentation. For more information on advanced search terms see here.

## Encodings
SWAPI provides two encodings for you to render the data with:

### JSON
JSON is the standard data format provided by SWAPI by default.

### Wookiee
Wookiee is for our tall hairy allies who speak Wookiee, this encoding is identical to JSON except with wookiee translations.

Using the wookiee renderer is easy, just append ?format=wookiee to your urls:

https://swapi.co/api/planets/1/?format=wookiee

## Resources
Root
The Root resource provides information on all available resources within the API.

Example request:

http https://swapi.co/api/
Example response:

HTTP/1.0 200 OK
Content-Type: application/json
{
    "films": "https://swapi.co/api/films/",
    "people": "https://swapi.co/api/people/",
    "planets": "https://swapi.co/api/planets/",
    "species": "https://swapi.co/api/species/",
    "starships": "https://swapi.co/api/starships/",
    "vehicles": "https://swapi.co/api/vehicles/"
}
Attributes:

films string -- The URL root for Film resources
people string -- The URL root for People resources
planets string -- The URL root for Planet resources
species string -- The URL root for Species resources
starships string -- The URL root for Starships resources
vehicles string -- The URL root for Vehicles resources
