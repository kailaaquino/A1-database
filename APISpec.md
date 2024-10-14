# API Specification for A1 Game



The API calls are made in this sequence when playing the game:
1. get name and password (log in)  ### 1.1
2. post name and password (sign up)  ### 1.2
3. get personal scores        ### 2.1
4. post score                 ### 2.2
5. post achievements
6. get past achievements 
7. get leaderboard
8. delete user

## 1. Player Login

### 1.1. Get User and Password - `/play/?username=yourUsername&password=yourPassword` (GET)

**Request**:

```json
[
  {
    "username": "string",
    "password": "string"
  }
  
]
```

**Response**:

```json
{
    "success": "boolean",
    "player_id": "number"
}

```

### 1.2. Search Player - `/play/{player_id}` (GET)

Retrieves player info. Displays user's high score, dates, achievements, and ranking on leader boards.

**Request**:

```json
[
  {
   "player_id": "number"
  }
  
]
```
**Response**:

```json
[
  {
    "high_score": "number",
    "dates": "string",
    "achievements": "string",
    "ranking": "number"
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
    "player_id": integer,
    "score_id": integer,
    "score": integer,
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
## 3. Bottling

The API calls are made in this sequence when the bottler comes:
1. `Get Bottle Plan`
2. `Deliver Bottles`

### 3.1. Get Bottle Plan - `/bottler/plan` (POST)

Gets the plan for bottling potions.

**Response**:

```json
[
    {
        "potion_type": [r, g, b, d], /* r, g, b, d are integers that add up to exactly 100 */
        "quantity": "integer"  /* Between 1 and 10000 */
    }
]
```

### 3.2. Deliver Bottles - `/bottler/deliver/{order_id}` (POST)

Posts delivery of potions. order_id is a unique value representing
a single delivery. 

**Request**:

```json
[
  {
    "potion_type": [r, g, b, d],
    "quantity": "integer"
  }
]
```


### 4. Admin Functions

### 4.1. Reset Shop - `/admin/reset` (POST)

A call to reset shop will delete all inventory and in-flight carts and reset gold back to 100. The
shop should take this as an opportunity to remove all of their inventory and set their gold back to
100 as well.

### 5. Info Functions

### .1. Current time - `/info/current_time` (POST)

Shares what the latest time (in game time) is. 

**Request**:

```json
[
  {
    "day": "string",
    "hour": "number"
  }
]
```

### 6. Audit Functions

### 6.1. Get Inventory Summary - `/inventory/audit` (GET)

Return a summary of your current number of potions, ml, and gold.

**Response**:
```json
{
  "number_of_potions": "number",
  "ml_in_barrels": "number",
  "gold": "number"
)
```  

### 6.2 Get capacity purchase plan - `/inventory/plan` (POST)

What additional potion or ML capacity the shop would like to buy. Called once a day.
You start with 1 capacity of potion and 1 capacity of ml storage. Each potion capacity
allows 50 potion storage. Each ml capacity allows 10k of ml storage.

**Response**:
```json
{
  "potion_capacity": "number",
  "ml_capacity": "number"
}
```

### 6.3 Deliver capacity purchased - `/inventory/deliver` (POST)

Delivers capacity purchased back to shop. Called when a capacity purchase succeeds.

**Request**:
```json
{
  "potion_capacity": "number",
  "ml_capacity": "number"
}
```