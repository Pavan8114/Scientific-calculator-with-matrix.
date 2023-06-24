# Scientific-calculator-with-matrix.
The Scientific Calculator program is a versatile tool for mathematical calculations. With a user-friendly interface, it offers arithmetic operations, exponentiation, square root, logarithmic and trigonometric functions, and matrix operations.
import math
import numpy as np

def scientific_calculator():
    while True: 
        # Ask user to choose an operator
        print("\n****Scientific Calculator Menu****") 
        print("Choose a mathematical operator: ") 
        print("1 = Addition")
        print("2 = Subtraction")
        print("3 = Multiplication")
        print("4 = Division")
        print("5 = Raising a number to a power")
        print("6 = Square Root")
        print("7 = Logarithmic Functions")
        print("8 = Trigonometric Functions")
        print("9 = Matrix Operations")
        print("10 = Quit Calculator")
        
        # Receive user's input (must be an integer) 
        user_operator = input("Please select an option from 1-10: ")
        
        if not user_operator.isdigit():
            print("Invalid input. Please enter a number from 1-10.")
            continue
        
        user_operator = int(user_operator)
        
        if user_operator == 10:
            print("\n**Goodbye! Have a great day**")
            break
        
        # Addition, Subtraction, Multiplication
        if user_operator in [1, 2, 3]:
            n = int(input("Enter the number of operands: "))
            operands = [float(input("Please enter operand {}: ".format(i+1))) for i in range(n)]
            
            if user_operator == 1:
                result = sum(operands)
            elif user_operator == 2:
                result = operands[0] - sum(operands[1:])
            else:  # user_operator == 3
                result = np.prod(operands)
            
            print("Result: ", result)
            
            while True:
                choice = input("Do you want to perform more calculations? (y/n): ")
                if choice.lower() == "y":
                    n = int(input("Enter the number of operands: "))
                    new_operands = [float(input("Please enter operand {}: ".format(i+1))) for i in range(n)]
                    
                    if user_operator == 1:
                        result += sum(new_operands)
                    elif user_operator == 2:
                        result -= sum(new_operands)
                    else:  # user_operator == 3
                        result *= np.prod(new_operands)
                    
                    print("Result: ", result)
                elif choice.lower() == "n":
                    break
                else:
                    print("Invalid choice. Please enter 'y' or 'n'.")
        
        # Division
        elif user_operator == 4:
            try:
                dividend = float(input("Please enter the dividend: "))
                divisor = float(input("Please enter the divisor: "))
                result = dividend / divisor
                print("Result: ", result)
            except ZeroDivisionError:
                print("Error: **Cannot divide by zero**\n")
            except ValueError:
                print("Error: **Invalid input. Please enter numeric values**\n")
        
        # Raising a number to a power
        elif user_operator == 5:
            base = float(input("Please enter the base: "))
            exponent = float(input("Please enter the exponent: "))
            result = base ** exponent
            print("Result: ", result)
        
        # Square Root
        elif user_operator == 6:
            operand = float(input("Please enter the operand: "))
            result = math.sqrt(operand)
            print("Result: ", result)
        
        # Logarithmic Functions
        elif user_operator == 7:
            operand = float(input("Please enter the operand: "))
            result = math.log10(operand)
            print("Result: ", result)
        
        # Trigonometric Functions
        elif user_operator == 8:
            print("Choose a type of Trigonometric Function:")
            print("1. Trigonometric Function")
            print("2. Inverse Trigonometric Function")
            print("3. Hyperbolic Trigonometric Function")
            print("4. Inverse Hyperbolic Trigonometric Function")
            
            x = int(input("Please select an option [1-4]: "))
            
            # Trigonometric Function
            if x == 1:
                first_operand = input("Choose the trigonometric function for your equation:\n1. sin\n2. cos\n3. tan\nEnter the access number: ")
                
                def calculate_trigonometric_function(func):
                    while True:
                        print(f"{func}(second operand)")
                        second_operand = input("Please enter the second operand for your equation in degrees: ")
                        angle_rad = math.radians(float(second_operand))
                        result = getattr(math, func)(angle_rad)
                        print("Result:", result)
                        
                        while True:
                            print("Do you want to continue?")
                            choice = input("Enter [y/n]: ")
                            if choice.lower() == "y":
                                break
                            elif choice.lower() == "n":
                                return
                            else:
                                print("Please enter a valid selection [y/n]")
                
                if first_operand == "1":
                    calculate_trigonometric_function("sin")
                elif first_operand == "2":
                    calculate_trigonometric_function("cos")
                elif first_operand == "3":
                    calculate_trigonometric_function("tan")
            
            # Inverse Trigonometric Function
            elif x == 2:
                first_operand = input("Choose the Inverse trigonometric function for your equation:\n1. sin⁻¹\n2. cos⁻¹\n3. tan⁻¹\nEnter the access number: ")
                
                def calculate_inverse_trigonometric_function(func):
                    while True:
                        print(f"{func}(second operand)")
                        second_operand = input("Please enter the second operand for your equation: ")
                        result = getattr(np, func)(float(second_operand))
                        result = result * 180 / np.pi
                        print("Result: ", result, "degrees")
        
                        while True:
                            print("Do you want to continue?")
                            choice = input("Enter [y/n]: ")
        
                            if choice.lower() == "y":
                                break
                            elif choice.lower() == "n":
                                return
                            else:
                                print("Please enter a valid selection [y/n]")
                
                if first_operand == "1":
                    calculate_inverse_trigonometric_function("arcsin")
                elif first_operand == "2":
                    calculate_inverse_trigonometric_function("arccos")
                elif first_operand == "3":
                    calculate_inverse_trigonometric_function("arctan")
            
            # Hyperbolic Trigonometric Function
            elif x == 3:
                first_operand = input("Choose the Hyperbolic trigonometric function for your equation:\n1. sinh\n2. cosh\n3. tanh\nEnter the access number: ")
                
                def calculate_hyperbolic_trigonometric_function(func):
                    while True:
                        print(f"{func}(second operand)")
                        second_operand = input("Please enter the second operand for your equation in degrees: ")
                        angle_rad = math.radians(float(second_operand))
                        result = getattr(math, func)(angle_rad)
                        print("Result:", result)
                        
                        while True:
                            print("Do you want to continue?")
                            choice = input("Enter [y/n]: ")
                            if choice.lower() == "y":
                                break
                            elif choice.lower() == "n":
                                return
                            else:
                                print("Please enter a valid selection [y/n]")
                
                if first_operand == "1":
                    calculate_hyperbolic_trigonometric_function("sinh")
                elif first_operand == "2":
                    calculate_hyperbolic_trigonometric_function("cosh")
                elif first_operand == "3":
                    calculate_hyperbolic_trigonometric_function("tanh")
            
            # Inverse Hyperbolic Trigonometric Function
            elif x == 4:
                first_operand = input("Choose the Inverse Hyperbolic trigonometric function for your equation:\n1. sinh⁻¹\n2. cosh⁻¹\n3. tanh⁻¹\nEnter the access number: ")
                
                def calculate_inverse_hyperbolic_trigonometric_function(func):
                    while True:
                        print(f"{func}(second operand)")
                        second_operand = input("Please enter the second operand for your equation: ")
                        result = getattr(np, func)(float(second_operand))
                        result = result * 180 / np.pi
                        print("Result: ", result, "degrees")
        
                        while True:
                            print("Do you want to continue?")
                            choice = input("Enter [y/n]: ")
        
                            if choice.lower() == "y":
                                break
                            elif choice.lower() == "n":
                                return
                            else:
                                print("Please enter a valid selection [y/n]")
                
                if first_operand == "1":
                    calculate_inverse_hyperbolic_trigonometric_function("arcsinh")
                elif first_operand == "2":
                    calculate_inverse_hyperbolic_trigonometric_function("arccosh")
                elif first_operand == "3":
                    calculate_inverse_hyperbolic_trigonometric_function("arctanh")
        
        # Matrix Operations
        elif user_operator == 9:
            def matrix_operations():
                print("Matrix Operations")
                print("1. Matrix Addition")
                print("2. Matrix Subtraction")
                print("3. Matrix Multiplication")
                print("4. Trace of a Matrix")
                print("5. Determinant of a Matrix")
    
                matrix_option = int(input("Please select an option [1-5]: "))
                # Matrix Addition
                if matrix_option == 1:
                    matrix1 = np.zeros((3, 3))
                    matrix2 = np.zeros((3, 3))
    
                    print("Enter values for Matrix 1:")
                    for i in range(3):
                        for j in range(3):
                            matrix1[i, j] = float(input(f"Enter element [{i+1}, {j+1}]: "))
    
                    print("Enter values for Matrix 2:")
                    for i in range(3):
                        for j in range(3):
                            matrix2[i, j] = float(input(f"Enter element [{i+1}, {j+1}]: "))
    
                    result = matrix1 + matrix2
                    print("Result:")
                    print(result)

                # Matrix Subtraction
                elif matrix_option == 2:
                    matrix1 = np.zeros((3, 3))
                    matrix2 = np.zeros((3, 3))

                    print("Enter values for Matrix 1:")
                    for i in range(3):
                        for j in range(3):
                            matrix1[i, j] = float(input(f"Enter element [{i+1}, {j+1}]: "))
    
                    print("Enter values for Matrix 2:")
                    for i in range(3):
                        for j in range(3):
                            matrix2[i, j] = float(input(f"Enter element [{i+1}, {j+1}]: "))
    
                    result = matrix1 - matrix2
                    print("Result:")
                    print(result)

                # Matrix Multiplication
                elif matrix_option == 3:
                    matrix1 = np.zeros((3, 3))
                    matrix2 = np.zeros((3, 3))

                    print("Enter values for Matrix 1:")
                    for i in range(3):
                        for j in range(3):
                            matrix1[i, j] = float(input(f"Enter element [{i+1}, {j+1}]: "))

                    print("Enter values for Matrix 2:")
                    for i in range(3):
                        for j in range(3):
                            matrix2[i, j] = float(input(f"Enter element [{i+1}, {j+1}]: "))

                    result = np.dot(matrix1, matrix2)
                    print("Result:")
                    print(result)

                # Matrix Trace
                elif matrix_option == 4:
                    matrix = np.zeros((3, 3))
    
                    print("Enter values for the Matrix:")
                    for i in range(3):
                        for j in range(3):
                            matrix[i, j] = float(input(f"Enter element [{i+1}, {j+1}]: "))
    
                    trace = np.trace(matrix)
                    print("Trace:", trace)

                # Matrix Determinant
                elif matrix_option == 5:
                    matrix = np.zeros((3, 3))

                    print("Enter values for the Matrix:")
                    for i in range(3):
                        for j in range(3):
                            matrix[i, j] = float(input(f"Enter element [{i+1}, {j+1}]: "))

                    determinant = np.linalg.det(matrix)
                    print("Determinant:", determinant)
    
                else:
                    print("Invalid input. Please select a valid option from 1-5.")

            matrix_operations()
        
        else:
            print("Invalid input. Please select a valid option from 1-10.")

# Start the scientific calculator
scientific_calculator()
