# Task
- Create a program that obtains a users date of birth and calculates their age
- Format the output in a clean way to the user
- Do this first with hardcoded values
- Then with user inputs, calculating whether their birthday has passed this year
- Then using a library, print out the number of hours they've been alive
## Solutions
### First with hardcoded values
```
current_year = 2020  # Sets the current year so we can compare with their year of birth
year_of_birth = 1947  # Gets their year of birth so that we can output it and calculate their age
name = "Bill"  # Getting their name so that we can greet them appropriately in the message
# Calculate their age based on the difference between their year of birth and the current year
age = current_year - year_of_birth
print(f"OMG {name}, you are {age} years old so you were born in {year_of_birth}")
```
### Then with user input and increased accuracy
```
current_date = "03/11/2020"  # Sets the current date so that we can compare it with their date of birth
name = input("Please enter your name:  ")  # Getting the users name as input
# Getting their date of birth as an input. The format of this is import for the conditions below.
date_of_birth = input("Please enter your date of birth in DD/MM/YYYY format:  ")
if int(current_date[3:5]) < int(date_of_birth[3:5]):  # Checks if they've gotten to their birthday month yet
    age = int(current_date[6:]) - int(date_of_birth[6:]) - 1  # If not then they are one year younger
elif int(current_date[3:5]) == int(date_of_birth[3:5]):  # Checks if it is their birthday month now
    # If it is and they haven't reached their birthday yet then they are one year younger
    if int(current_date[0:2]) < int(date_of_birth[0:2]):
        age = int(current_date[6:]) - int(date_of_birth[6:]) - 1
# If these conditions have not been met then they must have already had their birthday
else:
    age = int(current_date[6:]) - int(date_of_birth[6:])
print(f"OMG {name}, you are {age} years old so you were born in {date_of_birth[6:]}")  # Output the string
```
### Finally using the datetime library to output how many hours the user has been alive
```
current_date = dt.datetime(2020, 11, 3)  # Sets the current date as a datetime value
# creates a datetime value for date of birth given the users previous input
date_of_birth = dt.datetime(int(date_of_birth[6:]), int(date_of_birth[3:5]), int(date_of_birth[0:2]))
# calculates the difference between the current date and the date of birth
difference = current_date - date_of_birth
# obtains the difference in a number of days and then multiplies that by 24 to obtain the number of hours
hours_alive = difference.days * 24
print(f"Wow, {name}! You've been alive for {hours_alive} hours!")  # Outputs the string
```