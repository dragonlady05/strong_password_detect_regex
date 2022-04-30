import re           

def passwordStrength():                          # Define function name
    passwordText = input ( 'Enter password: ' )  # Takes user input
    
    charRegex = re.compile ( r'(\w{8,})' )  # Matches any word character and at least 8 characters
    lowerRegex = re.compile ( r'[a-z]+' )   # Matches the lowercase alphabet
    upperRegex = re.compile ( r'[A-Z]+' )   # Matches the uppercase alphabet
    digitRegex = re.compile ( r'[0-9]+' )   # Matches digits 0-9
    spclcharRegex = re.compile ( r'[#?!@$%^&*-]+' )  # Matches any special characters

    strong_pass = True  # Set strong_pass to TRUE for successful input
    while strong_pass:  # Will repeat the statement while the condition is TRUE, and stops when the condition is FALSE
        if charRegex.findall (passwordText ) == []:     # findall searches the regex pattern across the target string and returns all matches
            print ( 'Password must contain at least 8 characters,Try again.' )  # If passwordText does not meet RegEx
            break       # Terminates the execution of the current loop and resumes execution of the next statement
        elif lowerRegex.findall (passwordText ) == []:  # Checks for lower case regex and if FALSE, it checks the condition of the next statement
            print ( 'Password must contain at least 1 lowercase character, Try again' )
            break
        elif upperRegex.findall ( passwordText ) == []: # Checks for upper cases regex
            print ( 'Password must contain at least 1 uppercase character, Try again.' )
            break
        elif digitRegex.findall ( passwordText ) == []: # Checks for digit regex
            print ( 'Password must contain at least 1 number. Try again.' )
            break
        elif spclcharRegex.findall ( passwordText ) == []: # Checks for special character regex
            print ( 'Password must contain at least 1 special character, Try again.' )
            break
        else:
            print ( 'Your password is strong.' )  # If the passwordText matches using RegEx
        strong_pass = False  # Set strong_pass to False if the password do not meet the condition
        break
    if strong_pass:  # Outside statement out of the while loop
        print ('Must contain at least 8 characters, 1 lowercase, 1 uppercase, 1 number and 1 special character. Try again.' )  # If passwordText does not meet RegEx patterns
        passwordStrength ()
passwordStrength ()

