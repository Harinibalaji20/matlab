def calculator():
        while True:
         try:
            num1 = float(input("Enter the first number: "))
            opt= input("Enter the opt (+, -, *, /): ")
            num2 = float(input("Enter the second number: "))
            outcome = 0
            #calculation based on the opt
            if opt == '+':
                outcome = num1 + num2
            elif opt == '-':
                outcome = num1 - num2
            elif opt == '*':
                outcome = num1 * num2
            elif opt == '/':
                if num2 == 0:
                    print("Error: Can't divided by 0")
                else:
                    outcome = num1 / num2
            else:
                print("Invalid opt. Please choose from +, -, *, /")
            print("The outcome is:",outcome)
         except ValueError:
            print("Invalid input. Please enter valid numbers")
         except Exception as e:
            print("An unexpected error occurred in except block",e) 
calculator()
