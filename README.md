# Alexa-DJ-Music-API
From the provided Flask code, the API expects the following types of calls and responses. Here's an explanation of each endpoint, the parameters required, and the expected response structure:

---

### 1. **`/get_playlist_info/`**
**Method:** `GET`  
**Description:** Retrieves information about a playlist by its ID.  

**Request Parameters:**
- `id` (str): The unique ID of the playlist to retrieve information for.

**Example Request:**
```http
GET /get_playlist_info/?id=PL1234567890abcdef
```

**Response:**
- A JSON object containing the playlist's ID and title.
```json
{
  "id": "PL1234567890abcdef",
  "title": "My Playlist"
}
```

---

### 2. **`/stream_playlist/`**
**Method:** `GET`  
**Description:** Streams a playlist by its ID, including details of the first track and the full playlist.  

**Request Parameters:**
- `id` (str): The unique ID of the playlist.

**Example Request:**
```http
GET /stream_playlist/?id=PL1234567890abcdef
```

**Response:**
- A JSON object with details of the first track and a list of tracks in the playlist.
```json
{
  "song_info": {
    "metadata": {
      "title": "Track 1",
      "artist": "Artist Name",
      "video_id": "abcd1234",
      "thumbnail": {
        "url": "https://example.com/thumbnail.jpg",
        "width": 1280,
        "height": 720
      }
    },
    "stream": {
      "audio_url": "https://audio-stream-url.com/stream.m4a"
    }
  },
  "playlist": [
    {
      "title": "Track 1",
      "artist": "Artist Name",
      "video_id": "abcd1234",
      "thumbnail": {
        "url": "https://example.com/thumbnail.jpg",
        "width": 1280,
        "height": 720
      }
    },
    {
      "title": "Track 2",
      "artist": "Another Artist",
      "video_id": "wxyz5678",
      "thumbnail": {
        "url": "https://example.com/thumbnail2.jpg",
        "width": 1280,
        "height": 720
      }
    }
  ]
}
```

---

### 3. **`/get_stream/`**
**Method:** `GET`  
**Description:** Fetches the audio stream URL for a specific video ID.  

**Request Parameters:**
- `video_id` (str): The unique video ID to retrieve the audio stream for.

**Example Request:**
```http
GET /get_stream/?video_id=abcd1234
```

**Response:**
- A JSON object containing the audio stream URL.
```json
{
  "audio_url": "https://audio-stream-url.com/stream.m4a"
}
```

---

### 4. **`/find_stream_list/`**
**Method:** `GET`  
**Description:** Searches for a stream list based on a query and filter.  

**Request Parameters:**
- `query` (str): The search term (e.g., song name, artist name, or album name).  
- `filter` (str): The type of search, which can be:
  - `songs`: Search for individual tracks.
  - `artists`: Search for tracks by an artist.
  - `albums`: Search for tracks in an album.

**Example Request:**
```http
GET /find_stream_list/?query=Imagine&filter=songs
```

**Response:**
- A JSON object containing the first track's metadata and stream URL, as well as a playlist of tracks matching the query.
```json
{
  "song_info": {
    "metadata": {
      "title": "Imagine",
      "artist": "John Lennon",
      "video_id": "abcd1234",
      "thumbnail": {
        "url": "https://example.com/thumbnail.jpg",
        "width": 1280,
        "height": 720
      }
    },
    "stream": {
      "audio_url": "https://audio-stream-url.com/stream.m4a"
    }
  },
  "playlist": [
    {
      "title": "Imagine",
      "artist": "John Lennon",
      "video_id": "abcd1234",
      "thumbnail": {
        "url": "https://example.com/thumbnail.jpg",
        "width": 1280,
        "height": 720
      }
    },
    {
      "title": "Jealous Guy",
      "artist": "John Lennon",
      "video_id": "wxyz5678",
      "thumbnail": {
        "url": "https://example.com/thumbnail2.jpg",
        "width": 1280,
        "height": 720
      }
    }
  ]
}
```

---

### Summary of Required User API Responses:
The user-provided API must support:
1. **Retrieving playlist details by ID.**
2. **Streaming playlists, including track metadata and stream URLs.**
3. **Fetching audio stream URLs for specific video IDs.**
4. **Searching and filtering tracks, artists, or albums with appropriate metadata and stream details.**

The response format should follow the JSON structures outlined above for compatibility with the Flask app.
