import random
def get_alex_choice():
    print("\n rock-paper-scissors")
    return random.choice(['rock', 'paper', 'scissors'])
def get_haru_choice():
    while True:
        haru_input = input("Enter your choice [rock, paper, or scissors]: ")
        if haru_input in ['rock', 'paper', 'scissors']:
            return haru_input 
        else:
            print("Invalid choice. Please enter 'rock', 'paper', or 'scissors'.")
def play_round(haru_scores, alex_scores):
    alex_choice = get_alex_choice()
    haru_choice = get_haru_choice()
    print(f"alex chose: {alex_choice}")
    print(f"haru chose: {haru_choice}")
    result = find_winner(haru_choice, alex_choice)
    print(result)
    if result == "haru win!":
        haru_scores += 1
    elif result == "alex wins!":
        alex_scores += 1
    return haru_scores, alex_scores
def find_winner(haru_choice, alex_choice):
    if haru_choice == alex_choice:
        return "It's a draw!"
    elif (haru_choice == 'rock' and alex_choice == 'scissors') or \
         (haru_choice == 'paper' and alex_choice == 'rock') or \
         (haru_choice == 'scissors' and alex_choice == 'paper'):
        return "haru win!"
    else:
        return "alex wins!"
def play():
    print("Welcome to Rock-Paper-Scissors!")
    haru_total_score = 0
    alex_total_score = 0
    round_number = 0
    while True:
        round_number+= 1
        print(f"\n~~~Round {round_number}~~~")
        haru_total_score, alex_total_score = play_round(haru_total_score, alex_total_score)
        print(f"Score: haru - {haru_total_score}, alex - {alex_total_score}")
        play_again = input("Do haru want to play again? (yes/no): ")
        if play_again != 'yes':
            break
    print("\n~~~Game Over!~~~")
    print(f"Final Score: haru - {haru_total_score}, alex - {alex_total_score}")
    if haru_total_score > alex_total_score:
        print("Congratulations haru! you won the game!")
    elif alex_total_score > haru_total_score:
        print("The alex won the game. Better luck next time haru!")
    else:
        print("The game ended in a draw!")
if __name__ == "__main__":
    play()
