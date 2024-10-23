## Example flow 1
 Alice loves to play video games and realizes that she hasn’t played one of her local classics in a long time. She had memory of creating an account on the game A1 when she was last playing and is aware that the game's database likely kept tabs on her old scores associated with her account. She wants to know if the username she remembers is still registered in the game and how well she played previously. She boots up A1, and selects the login button to check.
To do so, Alice: 
* Starts by inputting her username 
  * Calls /account/?username=yourUsername` (GET)
* Once the endpoint returns a success, she is logged in and decides to check on her saved information
* To check her stats from her previous runs she
  * Calls /account/{player_id}` (GET)
* She decides that she also wanted to know how much progress she made with the game achievements
* To check the achievements saved to her username she
  * Calls /achievements/history/{player_id} (GET)

She is happy to feel the nostalgia of logging back in and seeing her old scores still on the game, deciding to play again for old times sake.


## Example flow 2
 Abigail happened to leave her computer running while signed in to A1. Her little sibling found her computer with a very fun looking game on the screen. Very in control of their will, her little sibling had no choice but to start playing the game and did so rather unstrategically for a good few hours. The progress and statistics from those unsatisfactory games were irreversibly saved to Abigail's account. She lost her top ranking on the leaderboard and score average was reduced beyond repair. Abigail is quite frustrated and wants to delete her account to start fresh and build a more perfect score.
To do so, Abigail:
* Deletes her current account 
  * Calls  /account/delete/{username}
* To make a new account, she
  * Calls /account/?username=yourUsername
* To check that her old account was deleted she searches for her old username
  * Calls /account/{player_id} (GET)
* Which returns an error saying there is no such player in the database

After conforming that she has started anew with a blank slate, she begins the game as an experienced player and gets an even higher average than before.


## Example flow 3
Ozcar is a daily player of A1. He takes pride in being #1 on the leaderboard. He wants to check the leaderboard and make sure that he is still in first place.
To do so, Ozcar:
* He goes to the leaderboard
  * leaderboard/all_scores (GET)
* Enters username
  * account/?username=yourUsername (GET)
* Views list of personal score
  * /score/getScore/{player_id} (GET)

