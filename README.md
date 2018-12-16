# Documentation

## Introduction
​	Welcome to the SingerAPI, the [I-Am-a-Singer](https://en.wikipedia.org/wiki/I_Am_a_Singer_(Chinese_TV_series)) API! This is an api for the singers and songs information from Chinese TV series [I-Am-a-Singer](https://en.wikipedia.org/wiki/I_Am_a_Singer_(Chinese_TV_series)). Our project provides simple HTTP requests to access the related resources.

​	To get started, grab a cup of your favorite beverage and read following **Getting Started** section. 

## Getting started

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
All resources support JSON Schema. Making a request to /api/resource/schema will give you the details of that resource. This will allow you to programmatically inspect the attributes of that resource and their types.



## Searching
All resources support a search parameter that filters the set of resources returned. This allows you to make queries like:

http://127.0.0.1/singerapi/api/singers/?name=xxx

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

```shell
http http://127.0.0.1:8080/singerapi/api/seasons/1/
```

**Example response:**
```shell
{
	"title" : "我是歌手第一季",
	"broadcast time" : "2013.1.18-2013.4.12",
	"hosts" : "胡海泉/陈羽凡/沙宝亮/何炅/汪涵",
	"winner" : "羽泉",
	"singers" : "http://127.0.0.1/singerapi/api/seasons/1/singers/",
	"songs" : "http://127.0.0.1/singerapi/api/seasons/1/songs/",
	"url" : "http://127.0.0.1/singerapi/api/seasons/1/"
}
```

**Attributes:**

- `title` string -- The season title.
- `broadcast time` string -- The broadcasts time of this season.
- `hosts` string -- The hosts of this season.
- `winner` string -- The finals winner of this season.
- `singers` string -- The URL of singers joined to this season.
- `songs` string -- The URL of songs performed in thin season.
- `url` string -- The URL of this resource.

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
	"singer" : "张韶涵",
	"songs": {
		"阿刁" : "http://127.0.0.1:8080/singerapi/api/songs/?name=阿刁",
		"梦里花" : "http://127.0.0.1:8080/singerapi/api/songs/?name=梦里花",
		...
	},
	"url" : "http://127.0.0.1/singerapi/api/singers/?name=张韶涵"
}

```

**Attributes:**

- `singer` string -- The singer name.
- `songs` json-- All singer's contributed songs and corresponding URL.
- `url` string -- The URL of this resource.


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
	"release date": "xxxx",
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
	"title" : "夜夜夜夜",
	"singer" : "http://127.0.0.1:8080/singerapi/api/singers/2/",
	"duration" : "05:00"
	"album" : "我是歌手第一季 第10期",
	"season" : "我是歌手第一季"
	"url" : "http://127.0.0.1/singerapi/api/songs/1"
}

```

**Attributes:**

- `title` string -- The name of the specific song
- `singer` string -- The name of singer who performed the song in *I Am a Singer*.
- `duration` string -- The time of performing the song.
- `album` string -- The name of the album which the song released in.
- `season` string -- The season in which the song was performed in *I Am a Singer*.
- `url` string -- The URL of this resource.

**Search Fields:**

- `title`



> refs: [swapi](https://swapi.co/documentation)
