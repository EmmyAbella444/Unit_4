
# QUIZ 049
![Screen Shot 2023-03-30 at 15 53 47](https://user-images.githubusercontent.com/111819437/228753707-604b0dd5-f784-4994-9720-9cfc4c0db1a4.png)

## CODE
```.py
import sqlite3
from Secure_passwords import encrypt_password, check_password

# Define a class to handle the database
class database_handler:
    def __init__(self,namedb:str):
        # Connect to the database and create a cursor object
        self.connection = sqlite3.connect(namedb)
        self.cursor = self.connection.cursor()

    def search(self, query):
        # Execute the search query and return the result
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query):
        # Execute a query to modify the database (e.g. insert, update, delete)
        self.cursor.execute(query)
        # Commit the changes to the database
        self.connection.commit()

    def close(self):
        # Close the database connection
        self.connection.close()

# Create a database_handler object to work with the database
x = database_handler("bitcoin_exchange.db")

# Define a query to select all rows from the ledger table
query = "SELECT * from ledger"

# Execute the query and get the result
result = x.search(query)

# Initialize a variable to hold the total amount
total= 0

# Loop through each row in the result
for i in result:
    # Get the values for each column in the row
    id = i[0]
    sender_id = i[1]
    receiver_id = i[2]
    amount = i[3]
    signature = i[4]
    # Concatenate the values into a string for signature verification
    string = f"id {id},sender_id {sender_id},receiver_id {receiver_id},amount {amount}"
    # Verify the signature for the string using the check_password function
    if check_password(string,signature) == True:
        # If the signature is valid, add the amount to the total
        total+=amount

# Print the total amount
print("Total amount:", total)

# Close the database connection
x.close()
```
## EVIDENCE
![Screen Shot 2023-04-04 at 23 07 59](https://user-images.githubusercontent.com/111819437/229819112-090d1dc2-c11e-46c4-af3f-ebeb208406ef.png)


