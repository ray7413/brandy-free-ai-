# brandy(free ai❤️‍🩹)[WORK IN PROGRESS, NO FINISHED PRODUCT YET!!!]

*Your free AI... well, sort of. ❤️‍🩹*

![Brandy](https://i.ibb.co.com/XxV6ftg8/Screenshot-2026-10-28-181321.png)

Meet Brandy! He's a little service that listens to your requests, does what you ask, and sends a response back. You send something in, Brandy processes it, and hopefully, he sends something useful back.

No complicated stuff. Just you, your requests, and Brandy.

## 💌 How does Brandy work?

It's pretty simple:

1. **You send a request.** Tell Brandy what you want to send or ask for.
2. **Brandy checks your API key.** He's gotta make sure you're allowed in.
3. **Brandy does his thing.** He saves your data or retrieves the information you requested.
4. **Brandy replies.** You get a response back in JSON.

```text
You
 |
 |  "Hey Brandy, save this for me!"
 v
brandy(free ai❤️‍🩹)
 |
 |  Checks your API key
 |  Processes your request
 |  Talks to the database
 v
Your response ❤️‍🩹
```

Basically, Brandy is the middleman between you and his database. You don't need to access the database directly. Just talk to Brandy through his API.

## 🛠️ Getting started

You'll need Python installed on your computer.

### 1. Install the dependencies

```bash
pip install fastapi uvicorn requests
```

### 2. Give Brandy his secret key

On Windows PowerShell:

```powershell
$env:API_KEY = "your-secret-key"
```

On Linux or macOS:

```bash
export API_KEY="your-secret-key"
```

Keep this key private! Brandy needs it to recognize authorized requests.

### 3. Wake Brandy up

Run this in the folder containing `main.py`:

```bash
uvicorn main:app --reload
```

And just like that, Brandy is running at:

`http://127.0.0.1:8000`

Want to see what he can do? Visit:

**http://127.0.0.1:8000/docs**

That's Brandy's interactive playground, where you can send requests and see his replies.

## 💬 Talking to Brandy

Brandy understands HTTP requests. For now, he has two main jobs: remembering things and telling you what he remembers.

Every request must include your API key:

```http
Authorization: Bearer YOUR_API_KEY
```

### 📥 Tell Brandy something — POST

Let's save your favorite programming language.

Send a `POST` request to:

`/memories`

With this JSON:

```json
{
  "key": "favorite_language",
  "value": "C++"
}
```

Brandy saves it to his database and replies:

```json
{
  "success": true,
  "id": 1
}
```

Aww, he remembered. ❤️‍🩹

### 📤 Ask Brandy what he remembers — GET

Send a `GET` request to:

`/memories`

Brandy looks through his database and replies with the saved information:

```json
{
  "memories": [
    {
      "id": 1,
      "key": "favorite_language",
      "value": "C++"
    }
  ]
}
```

He remembers things even after you restart the server, because the data is stored in SQLite.

### 🔎 Ask about one specific memory

Send a `GET` request to:

`/memories/1`

Brandy retrieves the record with ID `1`, if it exists.

## 🐍 Talking to Brandy with Python

You don't have to use the interactive docs. Your own programs can talk to him, too!

```python
import requests

BRANDY = "http://127.0.0.1:8000"
API_KEY = "your-secret-key"

headers = {
    "Authorization": f"Bearer {API_KEY}"
}

# Tell Brandy something
response = requests.post(
    f"{BRANDY}/memories",
    headers=headers,
    json={
        "key": "mood",
        "value": "surviving another day"
    }
)

print("Brandy says:", response.json())

# Ask Brandy what he remembers
response = requests.get(
    f"{BRANDY}/memories",
    headers=headers
)

print("Brandy remembers:", response.json())
```

Brandy's replies are JSON, so your program can read them, process them, and do whatever it needs to do next.


## ❤️‍🩹 Final words

Brandy isn't the smartest AI out there. In fact, he isn't really an AI yet.

But he's ours.

A little API that listens, remembers, and responds.

**One request at a time. One memory at a time.**

*brandy(free ai❤️‍🩹) — because sometimes, all you need is someone who remembers.*
