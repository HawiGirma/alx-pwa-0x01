# alx-project-0x14

This project demonstrates how to read and apply API documentation effectively by integrating with the **MoviesDatabase API**.  
The goal is to understand the API's endpoints, authentication, and response formats to use it correctly in TypeScript or JavaScript applications.

---

## API Overview

The **MoviesDatabase API** provides developers with access to a large database of movies, TV shows, and celebrity information.  
Key features include:

- Search for movies, TV shows, or people by title or ID.
- Retrieve detailed metadata (title, genres, release dates, posters, ratings).
- Fetch cast and crew details for any movie or TV show.
- Get random titles or browse through curated lists like trending and top-rated.
- Access both images and textual descriptions.

---

## Version

**API Version:** `v1`  
Reference: [MoviesDatabase API on RapidAPI](https://moviesdatabase.p.rapidapi.com/)

---

## Available Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET`  | `/titles` | Returns a list of movies and TV shows with optional filters (genre, year, etc.). |
| `GET`  | `/titles/{id}` | Retrieves full details about a movie or TV show using its unique ID. |
| `GET`  | `/titles/search/title/{title}` | Searches for a movie or TV show by its title text. |
| `GET`  | `/titles/random` | Returns a random movie or TV show entry. |
| `GET`  | `/titles/series/{id}` | Retrieves series details including seasons and episodes. |
| `GET`  | `/titles/{id}/cast` | Retrieves cast members for the given title. |
| `GET`  | `/titles/{id}/crew` | Retrieves crew members for the given title. |

---

## Request and Response Format

### Example Request – Search by Title
```http
GET https://moviesdatabase.p.rapidapi.com/titles/search/title/inception
X-RapidAPI-Key: YOUR_API_KEY
X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
Example Response
json
Copy
Edit
{
  "results": [
    {
      "id": "tt1375666",
      "titleText": { "text": "Inception" },
      "releaseYear": { "year": 2010 },
      "primaryImage": {
        "url": "https://m.media-amazon.com/images/M/MV5BMm.jpg",
        "caption": { "plainText": "Inception Poster" }
      }
    }
  ]
}
```
### Notes:

All responses are in JSON format.

Optional query parameters can be used to refine results (genre, year, limit, etc.).



## Authentication

The MoviesDatabase API is hosted on RapidAPI.  
To use it, you must:

- Create a free account at RapidAPI.
- Subscribe to the MoviesDatabase API.
- Include these headers with every request:

```http
X-RapidAPI-Key: YOUR_API_KEY
X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
```


## Error Handling
Common error responses:

401 Unauthorized – Missing or invalid API key.

```json

{ "message": "You are not subscribed to this API." }
```
429 Too Many Requests – Rate limit exceeded.

```json
{ "message": "You have exceeded your monthly quota." }
```


## Best Practices:

- Always check HTTP status codes.

- Implement retries for temporary failures.

For 429 errors, wait before retrying to avoid bans.



## Usage Limits and Best Practices
- Rate Limits: Depend on your RapidAPI subscription tier (free plans may allow ~500 requests/month).

### Tips:

- Cache frequent requests to save API calls.

- Request only necessary fields to improve performance.

- Use pagination when working with large datasets.

- Monitor API usage in your RapidAPI dashboard.

# Resources
- API Documentation: https://moviesdatabase.p.rapidapi.com/
- RapidAPI: https://rapidapi.com/
