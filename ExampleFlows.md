## Example flow 1
 Alice loves to play video games and realizes that she hasn’t played one of her local classics in a long time. She had memory of creating an account on the game A1 when she was last playing and is aware that the game's database likely kept tabs on her old scores associated with her account. She wants to know if the username she remembers is still registered in the game and how well she played previously. She logs into A1 to find out.
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
Ozcar is a daily player of A1. He takes pride in being #1 on the leaderboard. He wants to check the leaderboard and make sure that he is still in first place.
To do so, Ozcar:
* He goes to the leaderboard
  * leaderboard/all_scores (GET)
* Enters username
  * account/?username=yourUsername (GET)
* Views list of personal score
  * /score/getScore/{player_id} (GET)

