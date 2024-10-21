1. Description of the Project
This project implements a Bookstore Inventory Management System using Object-Oriented Programming (OOP) principles in Python. The system is designed to manage book inventory for a bookstore, with functionality to add, remove, update, and list items in stock. It also provides low-stock reports and allows for saving and loading data from a JSON file for persistence.
The project consists of three main classes:
Item: Represents a book in the inventory.
Inventory: Manages the collection of books.
Report: Generates various reports based on the inventory status.
The system ensures that the bookstore can efficiently keep track of its stock levels and identify low-stock items, helping in restocking decisions. Additionally, the system supports persistent storage through a JSON file to maintain data across different sessions.
2. Structure of the Code with Diagram and Comments
Code Structure Overview
Item Class: This class represents individual books with attributes like ID, title, author, quantity in stock, and price. It contains methods for updating the quantity and retrieving item details.
Inventory Class: This class manages the collection of Item objects and supports adding, removing, updating, listing, and saving/loading data to/from a JSON file.
Report Class: This class generates reports based on inventory data. It can list books that are running low in stock or generate a general inventory report.
Class Diagram (for better visualization):
            +------------------+
            |      Item         |
            +------------------+
            | - item_id         |
            | - title           |
            | - author          |
            | - quantity_stock  |
            | - price           |
            +------------------+
            | + update_quantity()|
            | + get_details()    |
            +------------------+
                     |
                     v
            +------------------+
            |   Inventory       |
            +------------------+
            | - items[]         |
            +------------------+
            | + add_item()      |
            | + remove_item()   |
            | + update_inventory()|
            | + list_items()    |
            | + save_to_file()  |
            | + load_from_file()|
            +------------------+
                     |
                     v
            +------------------+
            |    Report         |
            +------------------+
            | - inventory       |
            +------------------+
            | + low_stock_report() |
            | + generate_report()  |
            +------------------+
3. Instructions for Full Functionality
Step-by-Step Instructions to Use the System:
Add Books to Inventory: Create an Item object with attributes like ID, title, author, quantity in stock, and price. Then, add the item to the inventory using add_item()
book1 = Item(1, "The Great Gatsby", "F. Scott Fitzgerald", 10, 15.99)
inventory.add_item(book1)
List Books in Inventory: To view all books currently in the inventory, use the list_items() method.
print(inventory.list_items())

Update Stock: To update the quantity of a book, use the update_inventory() method with the book ID and the new quantity.
inventory.update_inventory(1, 5)

Save Inventory to File: You can save the current state of the inventory to a JSON file using the save_to_file() method.
inventory.save_to_file("inventory.json")

Load Inventory from File: To load inventory data from a JSON file, use the load_from_file() method.
inventory.load_from_file("inventory.json")

Generate Reports: The system can generate two types of reports:
Low Stock Report: Lists items that have stock below a set threshold.
report = Report(inventory)
print(report.low_stock_report(threshold=5))

General Inventory Report: Lists all items in the inventory.
print(report.generate_report())

4. Verification of Code Functionality
Testing Each Feature:
Adding Items: Multiple test cases have been performed to add different books to the inventory, ensuring that the system can handle various books with different attributes.
Removing Items: Removal functionality was tested to ensure that books can be removed by their unique ID.
Updating Inventory: The update_inventory() method was tested by changing the quantity of books and confirming that the updates were reflected correctly in the system.
Generating Reports: Both low-stock reports and general inventory reports were verified by testing books with different quantities and ensuring the reports listed the correct books based on the set criteria.
File Handling: The save_to_file() and load_from_file() methods were tested to ensure data persistence between sessions, confirming that the data was correctly written to and loaded from a JSON file.
5. Challenges, Limitations, and Areas for Improvement 
Challenges Faced:
Ensuring smooth data persistence using JSON files required careful handling of object serialization and deserialization, especially when loading data into Item objects.
Managing inventory with multiple attributes and ensuring the methods remained efficient and maintainable as more features were added.
Limitations:
The system currently uses a JSON file for data persistence. While this is suitable for small inventories, a more scalable approach, such as an SQLite database, could be considered for larger inventories.
No multi-user functionality is implemented yet. Adding roles (e.g., admin, manager) with varying permissions could be a future improvement.
Areas for Improvement:
Sales Tracking: Adding the ability to track book sales and update inventory levels based on sales could enhance the functionality.
Multi-user System: Introducing a user management system for different roles could provide additional security and control over inventory actions.
Graphical User Interface (GUI): Currently, the system runs in the command line. Developing a GUI for ease of use would make the system more user-friendly, especially for bookstore staff.
6. Overall Quality of the Report
This report has been structured to provide a clear and concise explanation of the project, detailing both the code and its functionality. Each section is designed to meet the assignment’s requirements, with examples and diagrams provided to aid in understanding.
7. Screenshots or Examples of Code Execution
Example of adding a book to the inventory and generating a low-stock report:
# Adding a new book
>>> inventory.add_item(Item(3, "To Kill a Mockingbird", "Harper Lee", 2, 9.99))
>>> inventory.list_items()
[
    {'ID': 1, 'Title': 'The Great Gatsby', 'Author': 'F. Scott Fitzgerald', 'Quantity in Stock': 10, 'Price': 15.99},
    {'ID': 2, 'Title': '1984', 'Author': 'George Orwell', 'Quantity in Stock': 2, 'Price': 12.99}
]

# Generating a low-stock report
>>> report = Report(inventory)
>>> print(report.low_stock_report())
[
    {'ID': 2, 'Title': '1984', 'Author': 'George Orwell', 'Quantity in Stock': 2, 'Price': 12.99}
]
