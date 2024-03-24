import random

def get_user_choice():
    while True:
        user_choice = input("Enter your choice (rock, paper, or scissors): ").strip().lower()
        if user_choice in ["rock", "paper", "scissors"]:
            return user_choice
        else:
            print("Invalid choice. Please enter rock, paper, or scissors.")

def get_computer_choice():
    return random.choice(["rock", "paper", "scissors"])

def determine_winner(user_choice, computer_choice):
    if user_choice == computer_choice:
        return "It's a tie!"
    elif (user_choice == "rock" and computer_choice == "scissors") or \
         (user_choice == "paper" and computer_choice == "rock") or \
         (user_choice == "scissors" and computer_choice == "paper"):
        return "You win!"
    else:
        return "Computer wins!"

def play_game():
    user_wins = 0
    computer_wins = 0
    rounds = 0

    while True:
        user_choice = get_user_choice()
        computer_choice = get_computer_choice()

        print(f"You chose {user_choice}. The computer chose {computer_choice}.")

        winner = determine_winner(user_choice, computer_choice)
        print(winner)

        if "You win" in winner:
            user_wins += 1
        elif "Computer wins" in winner:
            computer_wins += 1

        rounds += 1
        play_again = input("Do you want to play again? (yes/no): ").strip().lower()
        if play_again != "yes":
            print(f"Game over! You won {user_wins} times, computer won {computer_wins} times, and {rounds - user_wins - computer_wins} games ended in a tie.")
            break

# Play the game
play_game()
