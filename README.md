# 🎵 Groupie Tracker Teasers API

A simple static JSON API hosted on GitHub Pages.  
It contains basic information about music artists such as their **name**, **genres**, **top songs**, **teaser**, and an **image URL**.

---

## 📂 Base URL

https://nobleenia.github.io/groupietracker-teasers/data.json

---

## 📑 Example Response

```json
[
  {
    "id": 1,
    "name": "Queen",
    "genres": ["rock", "glam rock", "hard rock"],
    "top_songs": ["Bohemian Rhapsody", "We Will Rock You", "Don't Stop Me Now"],
    "teaser": "British rock icons with stadium-sized anthems.",
    "image": "https://i.scdn.co/image/ab6761610000e5eb1df43e72c8822ac2f1cfa3df"
  }
]
```
---

## 🚀 How to Use

You can fetch the JSON file directly with any HTTP client.

**CLI (cURL)**
```bash
curl https://nobleenia.github.io/groupietracker-teasers/data.json
```

Pretty-print with jq (install it first with sudo apt install jq or brew install jq):
```bash
curl -s https://nobleenia.github.io/groupietracker-teasers/data.json | jq
```

**JavaScript (Fetch API)**
```js
fetch("https://nobleenia.github.io/groupietracker-teasers/data.json")
  .then(res => res.json())
  .then(data => console.log(data));
```

**Python (Requests)**
```python
import requests

url = "https://nobleenia.github.io/groupietracker-teasers/data.json"
data = requests.get(url).json()
print(data)
```

**Go (net/http + encoding/json)**
```go
package main

import (
    "encoding/json"
    "fmt"
    "net/http"
)

type Artist struct {
    ID       int      `json:"id"`
    Name     string   `json:"name"`
    Genres   []string `json:"genres"`
    TopSongs []string `json:"top_songs"`
    Teaser   string   `json:"teaser"`
    Image    string   `json:"image"`
}

func main() {
    resp, err := http.Get("https://nobleenia.github.io/groupietracker-teasers/data.json")
    if err != nil {
        panic(err)
    }
    defer resp.Body.Close()

    var artists []Artist
    if err := json.NewDecoder(resp.Body).Decode(&artists); err != nil {
        panic(err)
    }

    for _, a := range artists {
        fmt.Printf("🎤 %s (%s)\n", a.Name, a.Image)
    }
}
```

---
## 📌 Notes

This API is read-only (static data).

New artists or updates must be added manually in the JSON file.

No authentication required.

You are free to use this data for demos, projects, or learning.
