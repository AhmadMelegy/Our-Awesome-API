# Projects

## List All Projects

```http
GET /projects HTTP/1.1
Content-Type: application/json; charset=utf-8
Authorization: token YOUR_ACCESS_TOKEN
```

> The above command returns JSON structured like this:

```http
HTTP/1.1 206 Partial Content
Content-Type: application/json
```

```json
{
	"projects": [{
		"id": 1,
		"name": "Say what you see",
		"url": "http://api.lockscreen.com/v1/projects/1",
		"thumbnail_url": "http://www.lockscreen.com/projects_thumbnails/1.jpg",
		"owner": {
			"id": 11,
			"name": "Galileo Galilei",
			"url": "http://api.lockscreen.com/v1/users/11"
		},
		"created_at": "2008-01-14T04:33:35Z",
		"enrollment_count": 700,
		"contributions_count": 510,
		"category": {
			"id": 210,
			"name": "Visual",
			"url": "http://api.lockscreen.com/v1/categories/4"
		}
	}, {
		"id": 7,
		"name": "Show me a pet",
		"url": "http://api.lockscreen.com/v1/projects/7",
		"thumbnail_url": "http://www.lockscreen.com/projects_thumbnails/7.jpg",
		"owner": {
			"id": 41,
			"name": "Albert Einstein",
			"url": "http://api.lockscreen.com/v1/users/41"
		},
		"created_at": "2008-01-14T04:33:35Z",
		"enrollment_count": 1730,
		"contributions_count": 1542,
		"goal": 4000,
		"progress": 38.55,
		"category": {
			"id": 210,
			"name": "Visual",
			"url": "http://api.lockscreen.com/v1/categories/4"
		}
	}],
	"next_id": -1,
	"total": 2
}
```

This endpoint retrieves all projects.

### HTTP Request

`GET http://api.lockscreen.com/v1/projects`

### Optional Parameters

Parameter | Type | Value
--------- | ---- | -----
filter | string | `popular` / `latest`

<aside class="notice">
This action is paginated. See the pagination documentation for details.
</aside>

## Get a Specific Project

```http
GET /projects/:id HTTP/1.1
Content-Type: application/json; charset=utf-8
Authorization: token YOUR_ACCESS_TOKEN
```

> The above command returns JSON structured like this:

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

```json
{
	"id": 7,
	"name": "Show me a pet",
	"url": "http://api.lockscreen.com/v1/projects/7",
	"thumbnail_url": "http://www.lockscreen.com/projects_thumbnails/7.jpg",
	"owner": {
		"id": 41,
		"name": "Albert Einstein",
		"url": "http://api.lockscreen.com/v1/users/41"
	},
	"created_at": "2008-01-14T04:33:35Z",
	"enrollment_count": 1730,
	"contributions_count": 1542,
	"category": {
		"id": 210,
		"name": "Visual",
		"url": "http://api.lockscreen.com/v1/categories/4"
	},
	"description": "Take a photo for any pet you",
	"location": "All over the world",
	"results": "http://api.lockscreen.com/v1/projects/7/results",
	"stats": "http://api.lockscreen.com/v1/projects/7/stats"
}
```

This endpoint retrieves a specific project.

### HTTP Request

`GET http://api.lockscreen.com/v1/projects/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the project to retrieve

## Add project

```http
PUT /projects HTTP/1.1
Content-Type: application/json; charset=utf-8
Authorization: token YOUR_ACCESS_TOKEN
```
> TODO

## Search in projects

```http
GET /projects?search="pet" HTTP/1.1
Content-Type: application/json; charset=utf-8
Authorization: token YOUR_ACCESS_TOKEN
```
> The above command returns JSON structured like this:

```http
HTTP/1.1 206 Partial Content
Content-Type: application/json
```

```json
{
	"projects": [{
		"id": 7,
		"name": "Show me a pet",
		"url": "http://api.lockscreen.com/v1/projects/7",
		"thumbnail_url": "http://www.lockscreen.com/projects_thumbnails/7.jpg",
		"owner": {
			"id": 41,
			"name": "Albert Einstein",
			"url": "http://api.lockscreen.com/v1/users/41"
		},
		"created_at": "2008-01-14T04:33:35Z",
		"enrollment_count": 1730,
		"contributions_count": 1542,
		"category": {
			"id": 210,
			"name": "Visual",
			"url": "http://api.lockscreen.com/v1/categories/4"
		}
	}],
	"next_id": -1,
	"total": 1
}
```
This endpoint retrieves projects that has the value of the `search` parameter in its title.

### HTTP Request

`GET http://api.lockscreen.com/v1/projects/search?<word>`

### URL Parameters

Parameter | Description
--------- | -----------
word | The word that you search for in projects titles.

<aside class="notice">
This action is paginated. See the pagination documentation for details.
</aside>


## List results of a project

```http
GET /projects/<ID>/results HTTP/1.1
Content-Type: application/json; charset=utf-8
Authorization: token YOUR_ACCESS_TOKEN
```

> The above command returns various JSON structured, based on the project type
e.g if the project collects images the like this:

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

> TODO

This endpoint retrieves the contributions in a project.

### HTTP Request

`GET http://api.lockscreen.com/v1/projects/<ID>/results`

### URL Parameters

Parameter | Description
--------- | -----------
ID |ID of the project

<aside class="notice">
This action is paginated. See the pagination documentation for details.
</aside>

## List projects created by a specific user

```http
GET /users/<user-id>/created-projects HTTP/1.1
Content-Type: application/json; charset=utf-8
Authorization: token YOUR_ACCESS_TOKEN
```

> The above command returns JSON structured like this:

```http
HTTP/1.1 206 Partial Content
Content-Type: application/json
```

```json
{
	"projects": [{
		"id": 1,
		"name": "Say what you see",
		"url": "http://api.lockscreen.com/v1/projects/1",
		"thumbnail_url": "http://www.lockscreen.com/projects_thumbnails/1.jpg",
		"created_at": "2008-01-14T04:33:35Z",
		"enrollment_count": 700,
		"contributions_count": 510,
		"category": {
			"id": 210,
			"name": "Visual",
			"url": "http://api.lockscreen.com/v1/categories/4"
		}
	}]
}
```

This endpoint retrieves projects created by a specific user.

### HTTP Request

`GET /users/<user-id>/created-projects`

### URL Parameters

Parameter | Description
--------- | -----------
user-id | The ID of the user you want to retrieve the project he created

<aside class="notice">
This action is paginated. See the pagination documentation for details.
</aside>