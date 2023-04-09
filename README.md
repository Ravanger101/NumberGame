<hr>
<h1 align="center"><code>Ultimate Number Game</code></h1>
<hr>


## Preview Code:
```
from random import randint
attempts_list = []
def show_score():
	if len(attempts_list) <= 0:
		print("There is currently no high score, it's yours for the taking!")
	else:
		print(f"The current high score is {min(attempts_list)} attempts")
def start_game():
	random_number = randint(1, 10)
	print("Hello traveler! Welcome to the game of guesses!")
	player_name = input("What is your name? ")
	wanna_play = input(f"Hi, {player_name}, would you like to play the guessing game? (Enter Yes/No) ")
	attempts = 0
	show_score()
	while wanna_play.lower().startswith("y"):
		try:
			guess = input("Pick a number between 1 and 10 ")
			if int(guess) < 1 or int(guess) > 10:
				raise ValueError("Please guess a number within the given range")
			if int(guess) == random_number:
				print("Nice! You got it!")
				attempts += 1
				attempts_list.append(attempts)
				print(f"It took you {attempts} attempts")
				play_again = input("Would you like to play again? (Enter Yes/No) ")
				attempts = 0
				show_score()
				random_number = randint(1, 10)
				if play_again.lower().startswith("n"):
					print("That's cool, have a good one!")
					break
			elif int(guess) > random_number:
				print("It's lower")
				attempts += 1
			elif int(guess) < random_number:
				print("It's higher")
				attempts += 1
		except ValueError as err:
			print("Oh no, that is not a valid value. Try again...")
			print(f"({err})")
	else:
		print("That's cool, have a good one!")
if __name__ == '__main__':
	start_game()
  ```
