## Example flow 1
 Alice loves to play video games and hasn’t played A1 in a while. She wants to know if her username is still registered in the game and how well she played previously. She logs into A1 to find out.
To do so, Alice: 
* Starts by inputting her username 
  * Calls /account/?username=yourUsername` (GET)
* To check her stats from her previous runs
  * calls /account/{player_id}` (GET)  

## Example flow 2
 Abigail’s little sibling played the game on Abigail’s account. She lost her top ranking on the leaderboard. Abigail is frustrated and wants to delete her account and statistics, and then start fresh with a new account. 	
To do so, Abigail:
* Deletes her current account
  * Calls  /account/delete/{username}
* To make a new account, she
  * /account/?username=yourUsername


## Example flow 3
