# Python-Functions-
#Create a calculator program that allows the user to perform mathematical operations on two numbers using basic functions and a dictionary to store the operations. The program should also have the ability to continue calculations with the result of previous calculations.
#Instructions
#Create four basic mathematical functions: 'add', 'subtract', 'multiply', and 'divide' that take in two numbers and return the result of the operation.
#Create a dictionary 'operations' that assigns the functions to their corresponding operation symbols.
#Create a function 'calculator' that prompts the user to input the first number.
#Use a for loop to print the available operation symbols.
#Create a while loop that will continue to run until the user chooses to end the current calculation.
#Inside the while loop, prompt the user to select an operation symbol.
#Prompt the user to input the second number.
#Use the dictionary to retrieve the function that corresponds to the selected operation symbol and store it in a variable 'calculation_function'
#Perform the calculation by calling the 'calculation_function' on the two input numbers and store the result in a variable 'answer'.
#Print the equation and the result of the calculation.
#Ask the user if they would like to continue using the result as the first number for further calculations.
#If the user chooses to continue, update the 'num1' variable to the value of 'answer'.
#If the user chooses to start a new calculation, set the 'should_continue' variable to false and call the 'calculator' function to start a new calculation.


#Python Functions Checkpoint SOLUTION
# Basic mathematical functions
def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    if y != 0:
        return x / y
    else:
        print("Error: Cannot divide by zero.")
        return None

# Dictionary of operations
operations = {
    '+': add,
    '-': subtract,
    '*': multiply,
    '/': divide
}

# Calculator function
def calculator():
    num1 = float(input("Enter the first number: "))

    while True:
        print("Available operations:")
        for symbol in operations.keys():
            print(symbol, end=' ')
        print()

        operation_symbol = input("Choose an operation symbol (type 'end' to finish): ")

        if operation_symbol == 'end':
            break

        if operation_symbol not in operations:
            print("Invalid operation symbol. Please try again.")
            continue

        num2 = float(input("Enter the second number: "))

        calculation_function = operations[operation_symbol]
        answer = calculation_function(num1, num2)

        print(f"{num1} {operation_symbol} {num2} = {answer}")

        should_continue = input("Do you want to continue with the result? (yes/no): ").lower()

        if should_continue == 'yes':
            num1 = answer
        else:
            calculator()  # Start a new calculation

# Start the calculator
calculator()
