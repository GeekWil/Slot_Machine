import random

Max_lines = 5
Max_bet = 300
Min_bet = 1


ROWS = 5
COLS = 3

#The following represent the % of each letter appear in the slot machine
symbol_count = {
    "A": 10,
    "B": 20,
    "C": 30,
    "D": 40,
}

#The following represent the mutiplier when wining
symbol_value = { 
    "A": 20,
    "B": 15,
    "C": 10,
    "D": 5,
}

def check_win(columns, lines, bet, values):
    winning = 0
    win_lines = []
    for line in range(lines):
        symbol = columns[0][line]
        for column in columns:
            symbol_to_check = column[line]
            if symbol != symbol_to_check:
                break
        else: #if all the columns are equal, then that mean the player win
            winning += values[symbol] * bet
            win_lines.append(line + 1)
    
    
    return winning, win_lines


#5th
def get_slot_machine_spin(rows, cols, symbols):
    all_symbols = []
    for symbol, symbol_count in symbols.items():
        for _ in range(symbol_count):
            all_symbols.append(symbol)
    
    columns = []
    for _ in range(cols):
        column = []
        current_symbols = all_symbols[:]  # this will make a copy of all_symbols, and will not affect the original one
        for _ in range(rows):
            value = random.choice(current_symbols)
            current_symbols.remove(value)
            column.append(value)
        
        columns.append(column)
    
    return columns

#4th
def print_slot_machine(columns):
    for row in range(len(columns[0])):
        for y, column in enumerate(columns):
            if y != len(columns) - 1:
                print(column[row], end=" | ")
            else:
                print(column[row], end=" ")

        print()

#1st
def deposit():
    while True:
        amount = input("How much would you like to deposit? $")
        if amount.isdigit():
            amount = int(amount)
            if amount > 0:
                print(f'You have deposit ${amount} dollars.')
                break
            else:
                print("Amount must be greater than 0.")
        else:
            print("Please enter a valid number.")
    return amount

#2nd
def get_num_lines():
    while True:
        lines = input(f"Enter the number of lines to bet on (1-{Max_lines})? ")
        if lines.isdigit():
            lines = int(lines)
            if lines == 1:
                print('You bet 1 line.')
                break
            elif 1 <  lines <= Max_lines:
                print(f'You bet {lines} lines.')
                break
            else:
                print("Please enter a valid number of lines.")
        else:
            print("Please enter a valid number.")
    return lines

#3rd
def get_bet():
    while True:
        amount = input("How much would you like to bet on each line? $")
        if amount.isdigit(): 
            amount = int(amount)
            if Min_bet <= amount <= Max_bet:
                print(f'You have bet ${amount} dollars.')
                break
            else:
                print(f"Amount needs to be between ${Min_bet} - ${Max_bet}.")
        else:
            print("Please enter a valid number.")
    return amount



def spin(balance):
    lines = get_num_lines()
    #below function to check whether the player has enough balance.
    while True:
        bet = get_bet()
        total_bet = bet * lines

        if total_bet > balance:
            print(f"You don't have enough to bet that amount, your current balance is ${balance}")
        else:
            break
    ##############
    print("Your current status:")
    print(f"you are betting ${bet} on {lines} lines. Total bet is equal ${total_bet}.")
    print(balance, lines)

    slots = get_slot_machine_spin(ROWS, COLS, symbol_count)
    print_slot_machine(slots)
    winning, win_lines = check_win(slots, lines, bet, symbol_value)
    print(f"You won ${winning}.")
    print(f"You won on lines:", *win_lines)
    return winning - total_bet

def main():
    balance = deposit()
    while balance > 0:
        print(f"Current balacne is ${balance}")
        spin_result = input("Press enter to play (q to quit).")
        if spin_result == "q":
            break
        else:
            balance += spin(balance)

    print(f"You left with ${balance}")


main()
