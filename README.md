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
    "all seasons": "http://127.0.0.1/singerapi/api/seasons/",
    "specific season": "http://127.0.0.1/singerapi/api/seasons/{id}/",
    "singers in season": "http://127.0.0.1/singerapi/api/seasons/{id}/singers",
    "songs in season": "http://127.0.0.1/singerapi/api/seasons/{id}/songs",
    "specific singer": "http://127.0.0.1/singerapi/api/singers/?name={name}",
    "specific song": "http://127.0.0.1/singerapi/api/songs/?name={name}"
}

```

**Attributes:**

- `all seasons` string -- The URL root for all seasons resources
- `specific seasons` string -- The URL root for specific season resources
- `singers in seasons` string -- The URL root for all singers in specific season
- `songs in seansons` string -- The URL root for all songs in specific season
- `specific singer` string -- The URL root for specific singer resources
- `specific song` string -- The URL root for specific song resources

<br>

### All seasons

All URL to specific seasons in *I Am a Singer* .

**Endpoints**

- `/seasons/` -- get all the season resources

**Example request:**

```http
http http://127.0.0.1:8080/singerapi/api/seasons/
```

**Example response:**

```http
HTTP/1.0 200 OK
Content-Type: application/json
{
	"seasons" : {
        "我是歌手第一季" : "http://127.0.0.1:8080/singerapi/api/seasons/1/",
        "我是歌手第一季" : "http://127.0.0.1:8080/singerapi/api/seasons/2/",
        "我是歌手第一季" : "http://127.0.0.1:8080/singerapi/api/seasons/3/",
        "我是歌手第一季" : "http://127.0.0.1:8080/singerapi/api/seasons/4/",
        "我是歌手第一季(歌手2017)" : "http://127.0.0.1:8080/singerapi/api/seasons/5/",
        "我是歌手第一季(歌手2018)" : "http://127.0.0.1:8080/singerapi/api/seasons/6/"
	}
	"url" : "http://127.0.0.1/singerapi/api/seasons/"
}
```

**Attributes:**

- `seasons` json -- All seasons and corresponding URL in *I Am a Singer*. 
- `url` string -- The URL of this resource.

<br>

### Specific season

A Seasons resource is a specific *I Am a Singer* season.

**Endpoints**

- `/seasons/{id}/` -- get a specific season resource

**Example request:**

```http
http http://127.0.0.1:8080/singerapi/api/seasons/1/
```

**Example response:**

```http
HTTP/1.0 200 OK
Content-Type: application/json
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

### Singers in specific season

All singers performed in specific season in *I Am a Singer* .

**Endpoints**

- `/seasons/{id}/singers/` -- get all singers contributed in specific season

**Example request:**

```http
http http://127.0.0.1:8080/singerapi/api/seasons/1/singers/
```

**Example response:**

```http
HTTP/1.0 200 OK
Content-Type: application/json
{
	"season" : "我是歌手第一季"
	"singers" : {
        "羽泉" : "http://127.0.0.1:8080/singerapi/api/singers/?singer=羽泉",
    	"杨宗纬" : "http://127.0.0.1:8080/singerapi/api/singers/?singer=杨宗纬",
    	"林志炫" : "http://127.0.0.1:8080/singerapi/api/singers/?singer=林志炫"
    	...
	}
	"url" : "http://127.0.0.1:8080/singerapi/api/seasons/1/singers/"
}
```

**Attributes:**

- `season` string -- The name of this season.
- `singers` json -- All singers in thin season and corresponding URL.
- `url` string -- The URL of this resource.

<br>

### Songs in specific season

All songs performed in specific season in *I Am a Singer* .

**Endpoints**

- `/seasons/{id}/songs/` -- get all songs performed in specific season

**Example request:**

```http
http http://127.0.0.1:8080/singerapi/api/seasons/1/songs/
```

**Example response:**

```http
HTTP/1.0 200 OK
Content-Type: application/json
{
	"season" : "我是歌手第一季",
	"songs" : {
        "浮夸" : "http://127.0.0.1:8080/singerapi/api/songs/?song=浮夸",
    	"相见恨晚" : "http://127.0.0.1:8080/singerapi/api/songs/?song=相见恨晚",
    	"往事随风" : "http://127.0.0.1:8080/singerapi/api/songs/?song=往事随风",
    	...
	}
	"url" : "http://127.0.0.1:8080/singerapi/api/seasons/1/songs/"
}
```

**Attributes:**

- `season` string -- The name of this season.
- `songs` json -- All songs performed in this season and correspongding URL.
- `url` string -- The URL of this resource.

<br>

### Specific singer

A Singer resource is a *I Am a Singer* participated singer.

**Endpoints**

- `/singers/?singer={name}` -- get a specific singers resource

**Example request:**

```http
http http://127.0.0.1:8080/singerapi/api/singers/?singer=张韶涵
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

- `singer`

<br>

### Specific song

A Song resource is a song performed in *I Am a Singer* .

**Endpoints**

- `/songs/?song={name}` -- get a specific songs resource

**Example request:**

```http
http http://127.0.0.1:8080/singerapi/api/songs/?song=夜夜夜夜
```

**Example response:**

```http
HTTP/1.0 200 OK
Content-Type: application/json
{
	"song" : "夜夜夜夜",
    "singer" : "林志炫",
    "duration" : "05:00"
	"album" : "我是歌手第一季 第10期",
	"season" : "我是歌手第一季"
	"url" : "http://127.0.0.1/singerapi/api/songs/?song=夜夜夜夜"
}

```

**Attributes:**

- `song` string -- The name of the specific song
- `singer` string -- The name of singer who performed the song in *I Am a Singer*.
- `duration` string -- The time of performing the song.
- `album` string -- The name of the album which the song released in.
- `season` string -- The season in which the song was performed in *I Am a Singer*.
- `url` string -- The URL of this resource.

**Search Fields:**

- `song`

<br>



> refs: https://swapi.co/documentation