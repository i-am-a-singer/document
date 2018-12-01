# Documentation

## Introduction
​	Welcome to the SingerAPI, the [I-Am-a-Singer](https://en.wikipedia.org/wiki/I_Am_a_Singer_(Chinese_TV_series)) API! This is an api for the singers and songs information from Chinese TV series [I-Am-a-Singer](https://en.wikipedia.org/wiki/I_Am_a_Singer_(Chinese_TV_series)). Our project provides simple HTTP requests to access the related resources.

​	To get started, grab a cup of your favorite beverage and read following **Getting Started** section. 

## Getting started

> TODO: complete installation instruction of api resource server. 
>
> TODO: complete HTTP response result.

​	Before type in our first eample, please ensure you have follow the installation instructions of SingerAPI api resource server and run server in local.

​	Then, let's make our first API request to the I-AM-A-SINGER API!

```shell
curl http://127.0.0.1:8080/singerapi/api/seasons
```

​	Then you will get response that:

```shell
...
```

​	Also you can open SingerAPI home site with server running in the local : http://127.0.0.1:8080/singerapi/



## Base URL
The Base URL is the root URL for all of the API, if you ever make a request to swapi and you get back a 404 NOT FOUND response then check the Base URL first.

The Base URL for SingerAPI is:

http://127.0.0.1:8080/singerapi/api

The documentation below assumes you are prepending the Base URL to the endpoints in order to make requests.



## Rate limiting
Swapi has rate limiting to prevent malicious abuse (as if anyone would abuse Star Wars data!) and to make sure our service can handle a potentially large amount of traffic. Rate limiting is done via IP address and is currently limited to 10,000 API request per day. This is enough to request all the data on the website at least ten times over. There should be no reason for hitting the rate limit.

## Authentication
Swapi is a completely open API. No authentication is required to query and get data. This also means that we've limited what you can do to just GET-ing the data. If you find a mistake in the data, then tweet the author or email him.

JSON Schema
All resources support JSON Schema. Making a request to /api/<resource>/schema will give you the details of that resource. This will allow you to programmatically inspect the attributes of that resource and their types.



## Searching
All resources support a search parameter that filters the set of resources returned. This allows you to make queries like:

https://127.0.0.1/singerapi/api/singers/?search=r2

All searches will use case-insensitive partial matches on the set of search fields. To see the set of search fields for each resource, check out the individual resource documentation. For more information on advanced search terms see here.



## Encodings
SWAPI provides two encodings for you to render the data with:

### JSON
JSON is the standard data format provided by SingerAPI by default.

## Resources
Root
The Root resource provides information on all available resources within the API.

Example request:

```http
http 127.0.0.1:8080/singerapi/api
```


Example response:

```http


HTTP/1.0 200 OK
Content-Type: application/json
{
    "seasons": "http://127.0.0.1/singerapi/api/seasons/",
    "singers": "http://127.0.0.1/singerapi/api/singers/",
    "albums": "http://127.0.0.1/singerapi/api/albums/",
    "songs": "http://127.0.0.1/singerapi/api/songs/"
}

```

Attributes:

- `seasons` string -- The URL root for Seasons resources
- `singers` string -- The URL root for Singers resources
- `albums` string -- The URL root for Albums resources
- `songs` string -- The URL root for Songs resources