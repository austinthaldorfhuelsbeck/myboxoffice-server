### A REST API for serving MyBoxOffice data

# /films

## Available Methods:

### GET

Sample Request:
`GET /films`

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

### POST

Sample Request:
`POST /films`

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
# /films/:filmID

## Available Methods:

### GET

Sample Request:
`GET /films/1`

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

### PUT

Sample Request:
`PUT /films/1`

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

### DELETE

Sample Request:
`DELETE /films/1`

This method has no response body.

# /films/:filmID/genres

## Available Methods:

### GET

Sample Request:
`GET /films/1/genres`

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

### POST

Returns all genres for selected film.

Sample Request:
`POST /films/1/genres`

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

# /films/:filmID/genres/:genreID

## Available Methods:

### DELETE

Returns all genres for selected film.

Sample Request:
`DELETE /films/1/genres/1`

Sample Response:
```
[
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

# /films/:filmID/credits

## Available Methods:

### GET

Sample Request:
`GET /films/1/credits`

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

### POST

Sample Request:
`POST /films/1/credits`

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

# /films/:filmID/credits/:filmCreditID

## Available Methods:

### DELETE

Returns all credits for selected film.

Sample Request:
`DELETE /films/1/credits/1`

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
