# Documentation

## Introduction
​	Welcome to the SingerAPI, the [I-Am-a-Singer](https://en.wikipedia.org/wiki/I_Am_a_Singer_(Chinese_TV_series)) API! This is an api for the singers and songs information from Chinese TV series [I-Am-a-Singer](https://en.wikipedia.org/wiki/I_Am_a_Singer_(Chinese_TV_series)). Our project provides simple HTTP requests to access the related resources.

​	To get started, grab a cup of your favorite beverage and read following **Getting Started** section. 

## Getting started

> TODO: complete installation instruction of api resource server. 
>
> TODO: complete HTTP response result.

​	Before type in our first eample, please ensure you have follow the installation instructions of SingerAPI api resource server and run server in local.

​	Then, let's make our first API request to the SingerAPI with [httpie](https://github.com/jakubroztocil/httpie/)!

```shell
http http://127.0.0.1:8080/singerapi/api/seasons/
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
### API
The API resource provides information on all available resources within the API.

**Example request:**

```http
http 127.0.0.1:8080/singerapi/api
```

**Example response:**

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

**Attributes:**

- `seasons` string -- The URL root for Seasons resources
- `singers` string -- The URL root for Singers resources
- `albums` string -- The URL root for Albums resources
- `songs` string -- The URL root for Songs resources



### Seasons

A Seasons resource is a specific *I Am a Singer* season.

**Endpoints**

- `/seasons/` -- get all the seasons resources
- `/seasons/:id/` -- get a specific seasons resource

**Example request:**

```http
http http://127.0.0.1:8080/singerapi/api/seasons/1/
```

**Example response:**

```http

HTTP/1.0 200 OK
Content-Type: application/json
{
	"broadcast time": "January 18 – April 12, 2013",
	"broadcaster": "Hunan Television",
	"finals venue":"Hunan Broadcasting System",
	"host(s)": "Hu Haiquan (Episode 1, 3-10, Repechage, Semifinal); Chen Yufan (Episode 2); Sha Baoliang, He Jiong, Wang Han (Final Round)",
	"judges": "500 public audiences",
	"runner-up": "http://127.0.0.1/singerapi/api/singers/2/",
	"title": "I Am a Singer (season 1)",
	"season": 1,
	"singers": [
        "http://127.0.0.1/singerapi/api/singers/1/",
        "http://127.0.0.1/singerapi/api/singers/2/",
        ....
	],
	"winner": "http://127.0.0.1/singerapi/api/singers/1/",
	"url": "http://127.0.0.1/singerapi/api/seasons/1/"
}

```

**Attributes:**

- `broadcast time` string -- The broadcasts time of this season.
- `broadcaster` string -- The broadcaster of this season.
- `finals venue` string -- The finals venue of this season.
- `host(s)` string -- The host(s) of this season.
- `judges` string -- The judges of this season.
- `runner-up` string -- The finals runner-up of this season.
- `title` string -- The season title.
- `season` int -- The season number.
- `singers` array -- An array of URL of singers joined to this season.
- `winner` string -- The finals winner of this season.
- `url`: string -- The URL of this resource.

**Search Fields:**

- `title`

<br>

### Singers

A Singer resource is a *I Am a Singer* participated singer.

**Endpoints**

- `/singers/` -- get all the singers resources
- `/singers/:id/` -- get a specific singers resource

**Example request:**

```http
http http://127.0.0.1:8080/singerapi/api/singers/1/
```

**Example response:**

```http
HTTP/1.0 200 OK
Content-Type: application/json
{
	"albums": [
		"http://127.0.0.1:8080/singerapi/api/albums/1/",
		"http://127.0.0.1:8080/singerapi/api/albums/2/",
		...
	],
	"introduce": "xxxxxxx",
	"name": "xxx",
	"songs":[
		"http://127.0.0.1:8080/singerapi/api/songs/1/",
		"http://127.0.0.1:8080/singerapi/api/songs/2/",
		...
	],
	"url": "http://127.0.0.1/singerapi/api/albums/1/"
}

```

**Attributes:**

- `albums` array -- An array of  URL of the singer's contributed albums resource.
- `introduce` string -- The singer introduce.
- `name` string -- The singer name.
- `songs` array -- An array of URL of the singer's contributed songs.
- `url`: string -- The URL of this resource.

**Search Fields:**

- `name`

<br>

### Albums

A Album resource is an album released by the singer joined in *I Am a Singer* .

**Endpoints**

- `/albums/` -- get all the albums resources
- `/albums/:id/` -- get a specific albums resource

**Example request:**

```http
http http://127.0.0.1:8080/singerapi/api/albums/1/
```

**Example response:**

```http
HTTP/1.0 200 OK
Content-Type: application/json
{
	"introduce": "xxxxxxx",
	“release date": "xxxx",
	"published company": "xxx",
	"singers": [
		"http://127.0.0.1:8080/singerapi/api/singers/1/",
		"http://127.0.0.1:8080/singerapi/api/singers/2/",
		...
	],
	"songs":[
		"http://127.0.0.1:8080/singerapi/api/songs/1/",
		"http://127.0.0.1:8080/singerapi/api/songs/2/",
		...
	],
	"title": "xxx",
	"url": "http://127.0.0.1/singerapi/api/albums/1/"
}

```

**Attributes:**

- `introduce` string -- A brief introduce of the album.
- `release date` string -- The publishing date of the album.
- `published company` string -- The publishing company of the album.
- `singers` array -- An array of URL of the singers who makes this album.
- `songs` array -- An array of URL of the album's songs ocurred in *I Am a Singer*.
- `title` string -- The title of the album.
- `url`: string -- The URL of this resource.

**Search Fields:**

- `title`

<br>

### Songs

A Song resource is a song played in *I Am a Singer* .

**Endpoints**

- `/songs/` -- get all the songs resources
- `/songs/:id/` -- get a specific songs resource

**Example request:**

```http
http http://127.0.0.1:8080/singerapi/api/songs/1/
```

**Example response:**

```http
HTTP/1.0 200 OK
Content-Type: application/json
{
	"singers": [
		"http://127.0.0.1:8080/singerapi/api/singers/1/",
		"http://127.0.0.1:8080/singerapi/api/singers/2/",
		...
	],
	"albums":[
		"http://127.0.0.1:8080/singerapi/api/albums/1/",
		"http://127.0.0.1:8080/singerapi/api/albums/2/",
		...
	],
	"title": "xxx",
	"url": "http://127.0.0.1/singerapi/api/songs/1/"
}

```

**Attributes:**

- `singers` array -- An array of URL of the songs singer ocurred in *I Am a Singer*.
- `albums` array -- An array of URL of the albums that the song released in.
- `title` string -- The title of the song.
- `url`: string -- The URL of this resource.

**Search Fields:**

- `title`