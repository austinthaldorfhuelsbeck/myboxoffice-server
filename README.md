# myboxoffice-server
#### A REST API for serving MyBoxOffice data

## /films

### Available Methods:

#### GET /

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

#### POST /

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
Input:
GET /1
Output:
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

Input:
PUT /1
	{
		rating: 9
	}
Output:
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

Input:


Input:
GET /1/genres
Output:
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
	
Input:
POST /1/genres/3
Output:
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
	
Input:
DELETE /1/genres/1
Output:
	[
		{
			genreID: 8,
			name: "scifi",
			rating: 9,
			color: "#3e33f5"
		}
	]

Input:
GET /1/credits
Output:
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
