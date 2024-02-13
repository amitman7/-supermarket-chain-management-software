# supermarket-chain-management-software
This project focuses on managing data for supermarket chains. The assignment involved creating software that handles the information stored in a database. Developed using Python and SQLite

# General Description
We want to build software that manages supermarket chains, called BGU Mart. The software should support managing a large number of employees and the buying/selling of products. The software should also manage the inventory and thus contact various suppliers, who supply products. Sells and deliveries of products should be also registered and logged for tax purposes.

The software by implementing a tool using Python and SQLite.

# Method and Technical Description
We built a sqlite3 database that holds the employee, supplier, product, branch, and activity tables.

The database filename will be bgumart.db.


# The Database Structure
The database bgumart.db has five tables.

Employees: This table holds information about the employees.
Suppliers: This table holds information about the suppliers.
Products: This table holds information about the products.
Branches: This table holds information about the branches.
Activities: This table holds information about all activities of the chain including sales and deliveries.

# initiate.py
This module builds the database and inserts the initial data from the configuration file. When run, it will be given a configuration file as an argument. For example:

python3 initiate.py config.txt
If the database file already exists remove it.

Initiate.py should create a “fresh” database with the tables as specified, parse the configuration file, and store the data given in the configuration file in the database appropriately.


# action.py
This module manages the supermarket activities, i.e. sales and deliveries (buys). When run, it will be given an actions file as an argument. It will perform each action in the order it appears in the file and then exits.


# printdb.py
This module prints the database.

Suppose you are given the following configuration file config.txt and run python3 initiate.py config.txt.
python3 printdb.py will print the following.

### Activities Branches 

(1, 'New York', 50)

(2, 'Los Angeles', 60)

(3, 'Chicago', 40)


### Employees 

(101, 'John Smith', 50000.0, 1)

(102, 'Jane Doe', 60000.0, 1)

(103, 'Bob Johnson', 45000.0, 2)


### Products 

(1, 'Apple', 0.5, 10)

(2, 'Banana', 0.25, 20)

(3, 'Orange', 0.75, 15)


### Suppliers 

(1, 'Acme Inc.', '(123) 456-7890')

(2, 'XYZ Corp.', '(234) 567-8901')

(3, 'ABC Enterprises', '(345) 678-9012')



### Employees report 

Alice Brown 165000.0 Chicago 0

Alice Johnson 105000.0 Los Angeles 0

Alice Williams 55000.0 Los Angeles 0

Bob Davis 175000.0 Chicago 0










# Configuration and action Files
## Configuration file
Each line in the configuration file represents either an Employee(E), Supplier(S), Product(P) or Branch(C). 
For example:

B,3,Chicago,40 represents a branch with id 3 located in Chicago with 40 employees.

E,106,Sue Davis,75000,3 represents an employee with id 106, named Sue Davis with a 75000 yearly salary that is working in branch 3.

P,5,Mango,2,7 represents a product with id 5, its description is Mango, the price is 2 shekel and the quantity is 7.

S,6,Jkl Enterprises,(678) 901-2345 represents a supplier with id is 6, named Jkl Enterprises and its contact information is (678) 901-2345.

Note:

E, S, P, and B at the beginning of each input row define record types and should not be inserted into the database.
Employee IDs and Supplier IDs are unique, meaning an employee ID can not repeat itself as a supplier ID and vice versa.
(Employee-IDs ꓵ Supplier-IDs = Ø).

# Action file
Each line in the action file represents an activity. An activity can be either a sale or a supply arrival. When quantity < 0 it is a sale activity, when quantity > 0 it is a supply arrival, and quantity=0 is illegal. For example:

3, 500, 56, 20230110 represents that supplier 56 supplied 500 units of product 3 on 10/Jan/2023.

100, -500, 1234, 20230110 represents that employee 1234 sold 500 units of product 100 on 10/Jan/2023.

If the current product quantity is less than the quantity in the sale activity the action should be ignored. e.

### Development Environment
In This assignment we used Python 3.9 and sqlite3.



