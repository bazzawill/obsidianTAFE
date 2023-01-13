# Importance of test design phase
- Test case well designed
- 100% functional coverage
- Create and review test cases 

# Boundry Value Analysis (BVA)
- Test edge cases
	- Inside and outside boundries
- No need to test in the middle of boundry
	- Assume if it works for edge cases correctly it will work for centre

# Equivalence Class Partitioning
- What are the list of classes
	- Success
	- Fail
### Example:
A text field accepts input between 1, 10 (whole number)

| Class | pass/fail |
| --- | --- |
| -Infinity - 0 | Fail |
| 1 - 10 | pass |
| 11 - infinity | fail |
| Contains decimal | fail |
| Contains non number | fail | 


# Decision table based testing
- Cause and effect table
- Input combinations - expected outcomes
### Example
Software to check who should get covid 19 vaccine
**Rule:** Only people with age **> 60** or anyone  **>45** with *either* **diabities** or **hypertension** allowed vaccination
| - | Age >60 | Age >45 | Diabeties | Hypertension| Outcome |
| --- | --- | --- | --- | --- | --- |
| 1 | Y | - | - | - | Allowed |
| 2 | N | Y | Y | Y | Allowed |
| 3 | N | Y | Y | N | Allowed |
| 4 | N | Y | N | Y | Allowed |
| 5 | N | Y | N | N | Not Allowed |
| 6 | N | N | - | - | Not Allowed |

# State transition testing
- Software has finite states
- Tranition from one state to another occurs due to action of user
#### Example
- State
	- User successfully logged in True / False
- Based on state:
	- Show user welcome screen or error
	- Show user private records or error

# Error guessing testing technique
- Experience and knowlege will generate test cases such as
	- divide by zero
	- correct input type
