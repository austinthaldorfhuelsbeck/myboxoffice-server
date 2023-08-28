### A REST API for serving MyBoxOffice data

# /films

## Available Methods:

### GET /

Sample Request:
`GET /`

Sample Response:
```
[
	{
		filmID: 1,
		title: "The Matrix",
		year: 1999,
		watched: true,
		rating: 10,
		owned: false,
		imgURL: "thematrix.jpg",
		favorite: true,
		genres: [
			{
				genreID: 1,
				name: "action",
				rating: 6,
				color: "#156f3f"
			},
			{
				genreID: 8,
				name: "scifi",
				rating: 9,
				color: "#3e33f5"
			}
		]
	},
	...
]
```

### POST /

Sample Request Body:
```
{
	title: "Star Wars",
	year: 1977,
	imgURL: "starwars.jpg"
	genres: [8]
}
```
Sample Response:
```
{
	filmID: 2,
	title: "Star Wars",
	year: 1977,
	watched: false,
	rating: 0,
	owned: false,
	imgURL: "starwars.jpg",
	favorite: false,
	genres: [
		{
			genreID: 8,
			name: "scifi",
			rating: 9,
			color: "#3e33f5"
		}
	]
}
```

### GET /:filmID

Sample Request:
`GET /1`

Sample Response:
```
{
	filmID: 1,
	title: "The Matrix",
	year: 1999,
	watched: true,
	rating: 10,
	owned: false,
	imgURL: "thematrix.jpg",
	favorite: true,
	genres: [
		{
			genreID: 1,
			name: "action",
			rating: 6,
			color: "#156f3f"
		},
		{
			genreID: 8,
			name: "scifi",
			rating: 9,
			color: "#3e33f5"
		}
	]
}
```

### PUT /:filmID

Sample Request:
`PUT /1`

Sample Request Body:
```
{
	rating: 9
}
```

Sample Response:
```
{
	filmID: 1,
	title: "The Matrix",
	year: 1999,
	watched: true,
	rating: 9,
	owned: false,
	imgURL: "thematrix.jpg",
	favorite: true,
	genres: [
		{
			genreID: 1,
			name: "action",
			rating: 6,
			color: "#156f3f"
		},
		{
			genreID: 8,
			name: "scifi",
			rating: 9,
			color: "#3e33f5"
		}
	]
}
```

### DELETE /:filmID

Sample Request:
`DELETE /1`

This method has no response body.

### GET /:filmID/genres

Sample Request:
`GET /1/genres`

Sample Response:
```
[
	{
		genreID: 1,
		name: "action",
		rating: 6,
		color: "#156f3f"
	},
	{
		genreID: 8,
		name: "scifi",
		rating: 9,
		color: "#3e33f5"
	}
]
```

### POST /:filmID/genres

Returns all genres for selected film.

Sample Request:
`POST /1/genres`

Sample Request Body:
```
{
	genreID: 3
}
```

Sample Response:
```
[
	{
		genreID: 1,
		name: "action",
		rating: 6,
		color: "#156f3f"
	},
	{
		genreID: 8,
		name: "scifi",
		rating: 9,
		color: "#3e33f5"
	},
	{
		genreID: 3,
		name: "comedy",
		rating: 9,
		color: "#ffffff"
	}
]
```

### DELETE /:filmID/genres/:genreID

Returns all genres for selected film.

Sample Request:
`DELETE /1/genres/1`

Sample Response:
```
[
	{
		genreID: 8,
		name: "scifi",
		rating: 9,
		color: "#3e33f5"
	}
]
```

### GET /:filmID/credits

Sample Request:
`GET /1/credits`

Sample Response:
```
[
	{
		filmCreditID: 1,
		filmmaker: {
			filmmakerID: 1,
			name: "Keanu Reeves",
			rating: 10,
			imgURL: "keanureeves.jpg"
		},
		role: {
			roleID: 1,
			name: "Actor",
			color: "#12be29"
		}
	},
	{
		filmCreditID: 2,
		filmmaker: {
			filmmakerID: 2,
			name: "Lana Wachowski",
			rating: 8,
			imgURL: "lanawachowski.jpg"
		},
		role: {
			roleID: 4,
			name: "Director",
			color: "#798436"
		}
	}
]
```

### POST /:filmID/credits

Sample Request:
`POST /1/credits`

Sample Request Body:
```
{
	filmmaker: 3,
	role: 4
}
```

Sample Response:
```
[
	{
		filmCreditID: 1,
		filmmaker: {
			filmmakerID: 1,
			name: "Keanu Reeves",
			rating: 10,
			imgURL: "keanureeves.jpg"
		},
		role: {
			roleID: 1,
			name: "Actor",
			color: "#12be29"
		}
	},
	{
		filmCreditID: 2,
		filmmaker: {
			filmmakerID: 2,
			name: "Lana Wachowski",
			rating: 8,
			imgURL: "lanawachowski.jpg"
		},
		role: {
			roleID: 4,
			name: "Director",
			color: "#798436"
		}
	},
	{
		filmCreditID: 3,
		filmmaker: {
			filmmakerID: 3,
			name: "Lily Wachowski",
			rating: 8,
			imgURL: "lilywachowski.jpg"
		},
		role: {
			roleID: 4,
			name: "Director",
			color: "#798436"
		}
	}
]
```

### DELETE /:filmID/credits/:filmCreditID

Returns all credits for selected film.

Sample Request:
`DELETE /1/credits/1`

Sample Response:
```
[
	{
		filmCreditID: 2,
		filmmaker: {
			filmmakerID: 2,
			name: "Lana Wachowski",
			rating: 8,
			imgURL: "lanawachowski.jpg"
		},
		role: {
			roleID: 4,
			name: "Director",
			color: "#798436"
		}
	},
	{
		filmCreditID: 3,
		filmmaker: {
			filmmakerID: 3,
			name: "Lily Wachowski",
			rating: 8,
			imgURL: "lilywachowski.jpg"
		},
		role: {
			roleID: 4,
			name: "Director",
			color: "#798436"
		}
	}
]
```
