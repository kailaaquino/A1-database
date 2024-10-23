# API Specification for A1 Game



The API calls are made in this sequence when playing the game:
1. get name and password (connecting to player's account) (1.1)
2. post name and password (adding new player) (1.2)
3. get personal scores (2.1)
4. post score (2.2)
5. post achievements (3.1)
6. get past achievements (3.2)
7. get leaderboard (4)
8. delete user (5)

## 1. Player Account

### 1.1. Get User and Password - `/account/?username=yourUsername` (GET)

**Request**:

```json
[
  {
    "username": "string",
  }
  
]
```

**Response**:

```json
{
    "success": "boolean",
    "player_id": "integer"
}

```

### 1.2. Search Player - `/account/{player_id}` (GET)

Retrieves player info. Displays user's high score, dates, achievements, and ranking on leader boards.

**Request**:

```json
[
  {
   "player_id": "integer"
  }
  
]
```
**Response**:

```json
[
  {
    "high_score": "integer",
    "dates": "string",
    "achievements": "string",
    "ranking": "integer"
  }
  
]
```

## 2. Players' scores 

The API calls are made in this sequence the game is played:
1. `Post player's score `
2. `Get player's score`

### 2.1. POST Players Score - `/score/postScore/{player_id, score}` (POST)
Uploads the players score the to data base after playing the game, the score will have the players ID

**Request**:

```json
[
  {
    "player_id": "integer",
    "score_id": "integer",
    "score": "integer",
  }
]
```

**Response**:

```json
[
    {
         "success": boolean
    }
]
```

### 2.2. Get Players Previous scores - `/score/getScore/{player_id}` (GET)

Gets a list of all the previous scores associated with a players id.

**Request**:

```json
[
  {
    "player_id": integer
  }
]
```
**Response**:

```json
[
  {
    "player_id": integer,
    "score_id": integer,
    "score": integer,
  }
]
```
## 3. Achievements

This API call is made after finishing a game:
1. `Post New Achievements`

This API call is made when accessing achievements:
1. `Get Past Achievements`

### 3.1. Post New Achievements - `/achievements/new` (POST)

Posts player's achievements for this round. It is added to the achievements table.

**Request**:

```json
[
  {
    "player_id": "integer"
  }
]
```


**Response**:
```json
[
    {
        "achievement": "string" /* shouldn't be empty */
    }
]
```

### 3.2. Get Past Achievements - `/achievements/history/{player_id}` (GET)

Retrieves past achievements for a player_id. It should include the newest achievement. 

**Request**:

```json
[
  {
    "player_id": "integer"
  }
]
```


**Response**:

```json
[
    {
        "achievement": "string" /* shouldn't be empty */
    }
]
```


### 4. Leaderboard

### 4.1. Get Leaderboard - `/info/Leaderboard` (GET)

Return a list of the top 10 players

**Response**:
```json
  {
    "Top_Scores": "list",
    "rank": "integer",
    "username": "string",
    "score": "integer",
  },
 

```

### 5. Delete User

### 5.1. Delete User - `/info/Delete_username` (DELETE)

Delete a player account from the database

**request**
```json
{
  "username": "string"
}
```
**Response**:
```json

 {
  "success": "boolean",
}

```  


