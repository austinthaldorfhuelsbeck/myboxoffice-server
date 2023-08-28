### A REST API for serving MyBoxOffice data

# /films

## Available Methods:

### GET

#### Responds with a list of all films in the MyBoxOffice database.

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
	}
]
```

### POST

#### Accepts a film object to post with at least minimum required data and responds with the full film object on the server.

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

#### Responds with the film object at the referenced `filmID`.

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

#### Accepts a partial film object with at least one value to update and responds with the full updated film object on the server.

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

#### Deletes the film object at the referenced `filmID` and responds with a list of all remaining film objects on the server.

Sample Request:
`DELETE /films/1`

Sample Response:
```
[
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
]
```

# /films/:filmID/genres

## Available Methods:

### GET

#### Responds with a list of all genre objects associated with referenced `filmID`.

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

#### Accepts a genre object to post with at least minimum required data and responds with a list of all genre objects associated with referenced `filmID`.

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

#### Deletes the genre object at the referenced `genreID` and responds with a list of all remaining genre objects associated with referenced `filmID`.

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

#### Responds with a list of all credits associated with referenced `filmID`.

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
			roleID: 0,
			name: "Actor",
			color: "#12be29"
		},
		character: {
			characterID: 1,
			name: "Neo",
			color: "#798436",
			rating: 10
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

#### Accepts a filmCredit object with at least minimum required data and responds with a list of all credit objects associated with referenced `filmID`.

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
			roleID: 0,
			name: "Actor",
			color: "#12be29"
		},
		character: {
			characterID: 1,
			name: "Neo",
			color: "#798436",
			rating: 10
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

#### Deletes the credit object at the referenced `filmCreditID` and responds with a list of all remaining filmCredit objects associated with referenced `filmID`.

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



# /series

## Available Methods:

### GET

#### Responds with a list of all series objects on the server.

Sample Request:
`GET /series`

Sample Response:
```
[
	{
		seriesID: 1,
		title: "Game of Thrones",
		startYear: 2011,
		endYear: 2019,
		watched: true,
		rating: 7,
		owned: false,
		imgURL: "westeros.jpg",
		favorite: true,
		genres: [
			{
				genreID: 1,
				name: "action",
				rating: 6,
				color: "#156f3f"
			},
			{
				genreID: 10,
				name: "fantasy",
				rating: 9,
				color: "#678ff7"
			}
		]
	},
	...
]
```

### POST

#### Accepts a series object to post with at least minimum required data and responds with the full series object on the server.

Sample Request:
`POST /series`

Sample Request Body:
```
{
	title: "Futurama",
	startYear: 1999,
	endYear: 2013,
	imgURL: "futurama.jpg"
	genres: [3]
}
```
Sample Response:
```
{
	seriesID: 2,
	title: "Futurama",
	startYear: 1999,
	endYear: 2013,
	watched: false,
	rating: 0,
	owned: false,
	imgURL: "futurama.jpg",
	favorite: false,
	genres: [
		{
			genreID: 3,
			name: "comedy",
			rating: 9,
			color: "#ffffff"
		}
	]
}
```
# /series/:seriesID

## Available Methods:

### GET

#### Responds with the series object at the referenced `seriesID`.

Sample Request:
`GET /series/1`

Sample Response:
```
{
	seriesID: 1,
	title: "Game of Thrones",
	startYear: 2011,
	endYear: 2019,
	watched: true,
	rating: 7,
	owned: false,
	imgURL: "westeros.jpg",
	favorite: true,
	genres: [
		{
			genreID: 1,
			name: "action",
			rating: 6,
			color: "#156f3f"
		},
		{
			genreID: 10,
			name: "fantasy",
			rating: 9,
			color: "#678ff7"
		}
	]
}
```

### PUT

#### Accepts a partial series object with at least one value to update and responds with the full updated series object on the server.

Sample Request:
`PUT /series/2`

Sample Request Body:
```
{
	rating: 10,
	watched: true,
	owned: true,
	favorite: true
}
```

Sample Response:
```
{
	seriesID: 2,
	title: "Futurama",
	startYear: 1999,
	endYear: 2013,
	watched: true,
	rating: 10,
	owned: true,
	imgURL: "futurama.jpg",
	favorite: true,
	genres: [
		{
			genreID: 3,
			name: "comedy",
			rating: 9,
			color: "#ffffff"
		}
	]
}
```

### DELETE

#### Deletes the series object at the referenced `seriesID` and responds with a list of all remaining series objects on the server.

Sample Request:
`DELETE /series/1`

Sample Response:
```
[
	{
		seriesID: 2,
		title: "Futurama",
		startYear: 1999,
		endYear: 2013,
		watched: true,
		rating: 10,
		owned: true,
		imgURL: "futurama.jpg",
		favorite: true,
		genres: [
			{
				genreID: 3,
				name: "comedy",
				rating: 9,
				color: "#ffffff"
			}
		]
	}
]
```

# /series/:seriesID/genres

## Available Methods:

### GET

#### Responds with a list of all genre objects associated with referenced `seriesID`.

Sample Request:
`GET /series/1/genres`

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
		genreID: 10,
		name: "fantasy",
		rating: 9,
		color: "#678ff7"
	}
]
```

### POST

#### Accepts a genre object to post with at least minimum required data and responds with a list of all genre objects associated with referenced `seriesID`.

Returns all genres for selected series.

Sample Request:
`POST /series/1/genres`

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
		genreID: 10,
		name: "fantasy",
		rating: 9,
		color: "#678ff7"
	}
	{
		genreID: 3,
		name: "comedy",
		rating: 9,
		color: "#ffffff"
	}
]
```

# /series/:seriesID/genres/:genreID

## Available Methods:

### DELETE

#### Deletes the genre object at the referenced `genreID` and responds with a list of all remaining genre objects associated with referenced `seriesID`.

Sample Request:
`DELETE /series/1/genres/1`

Sample Response:
```
[
	{
		genreID: 10,
		name: "fantasy",
		rating: 9,
		color: "#678ff7"
	}
	{
		genreID: 3,
		name: "comedy",
		rating: 9,
		color: "#ffffff"
	}
]
```

# /series/:seriesID/credits

## Available Methods:

### GET

Sample Request:
`GET /series/1/credits`

Sample Response:
```
[
	{
		seriesCreditID: 1,
		filmmaker: {
			filmmakerID: 10,
			name: "Peter Dinklage",
			rating: 8,
			imgURL: "peterdinklage.jpg"
		},
		role: {
			roleID: 0,
			name: "Actor",
			color: "#12be29"
		},
		character: {
			characterID: 10,
			name: "Tyrion Lannister",
			color: "#ffffff",
			rating: 8
		}
	},
	{
		seriesCreditID: 2,
		filmmaker: {
			filmmakerID: 11,
			name: "Iain Glen",
			rating: 9,
			imgURL: "iainglen.jpg"
		},
		role: {
			roleID: 0,
			name: "Actor"
			color: "#12be29"
		},
		character: {
			characterID: 11,
			name: "Jorah Mormont",
			color: "#000000",
			rating: 9
		}
	}
]
```

### POST

#### Accepts a seriesCredit object with at least minimum required data and responds with a list of all credit objects associated with referenced `seriesID`.

Sample Request:
`POST /series/1/credits`

Sample Request Body:
```
{
	filmmaker: 12,
	role: 1,
	characters: [
		{
			characterID: 12,
			name: "Daenerys Targaryen",
			rating: 10
		}
	]
}
```

Sample Response:
```
[
	{
		seriesCreditID: 1,
		filmmaker: {
			filmmakerID: 10,
			name: "Peter Dinklage",
			rating: 8,
			imgURL: "peterdinklage.jpg"
		},
		role: {
			roleID: 0,
			name: "Actor",
			color: "#12be29"
		},
		character: {
			characterID: 10,
			name: "Tyrion Lannister",
			color: "#ffffff",
			rating: 8
		}
	},
	{
		seriesCreditID: 2,
		filmmaker: {
			filmmakerID: 11,
			name: "Iain Glen",
			rating: 9,
			imgURL: "iainglen.jpg"
		},
		role: {
			roleID: 0,
			name: "Actor"
			color: "#12be29"
		},
		character: {
			characterID: 11,
			name: "Jorah Mormont",
			color: "#000000",
			rating: 9
		}
	},
	{
		seriesCreditID: 3,
		filmmaker: {
			filmmakerID: 12,
			name: "Emilia Clarke",
			rating: 8,
			imgURL: "emiliaclarke.jpg"
		},
		role: {
			roleID: 0,
			name: "Actor"
			color: "#12be29"
		},
		character: {
			characterID: 12,
			name: "Daenerys Targaryen",
			color: "#000000",
			rating: 10
		}
	}
]
```

# /series/:seriesID/credits/:seriesCreditID

## Available Methods:

### DELETE

#### Deletes the credit object at the referenced `seriesCreditID` and responds with a list of all remaining seriesCredit objects associated with referenced `seriesID`.

Sample Request:
`DELETE /series/1/credits/1`

Sample Response:
```
[
	{
		seriesCreditID: 2,
		filmmaker: {
			filmmakerID: 11,
			name: "Iain Glen",
			rating: 9,
			imgURL: "iainglen.jpg"
		},
		role: {
			roleID: 0,
			name: "Actor"
			color: "#12be29"
		},
		character: {
			characterID: 11,
			name: "Jorah Mormont",
			color: "#000000",
			rating: 9
		}
	},
	{
		seriesCreditID: 3,
		filmmaker: {
			filmmakerID: 12,
			name: "Emilia Clarke",
			rating: 8,
			imgURL: "emiliaclarke.jpg"
		},
		role: {
			roleID: 0,
			name: "Actor"
			color: "#12be29"
		},
		character: {
			characterID: 12,
			name: "Daenerys Targaryen",
			color: "#000000",
			rating: 10
		}
	}
]
```

# /genres

## Available Methods:

### GET

#### Responds with a list of all genre objects on the server.

### POST

#### Accepts a genre object with at least minimum required data and responds with the full genre object on the server.

# /genres/:genreID

## Available Methods:

### GET

#### Responds with the genre object on the server associated with the referenced `genreID`.

### PUT

#### Accepts a partial genre object with at least one value to update and responds with the full updated genre object on the server.

### DELETE

#### Deletes the genre object associated with the referenced `genreID` and responds with a list of remaining genre objects on the server.

# /roles

## Available Methods:

### GET

#### Responds with a list of all role objects on the server.

### POST

#### Accepts a role object with at least minimum required data and responds with the full role object on the server.

# /roles/:roleID

## Available Methods:

### GET

#### Responds with the role object on the server associated with the referenced `roleID`.

### PUT

#### Accepts a partial role object with at least one value to update and responds with the full updated role object on the server.

### DELETE

#### Deletes the role object associated with the referenced `roleID` and responds with a list of remaining role objects on the server.

# /roles/0/characters

## Available Methods:

### GET

#### Responds with a list of all character objects

# /filmmakers
