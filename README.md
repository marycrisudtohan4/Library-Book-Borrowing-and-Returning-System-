# Library-Book-Borrowing-and-Returning-System-
THE PROPOSED LIBRARY BOOK BORROWING AND RETURNING SYSTEM AIMS TO ENHANCE THE EFFICIENCY OF SCHOOL LIBRARIES BY REPLACING MANUAL DATA RECORDING WITH A DIGITAL MANAGEMENT SYSTEM. 

from datetime import datetime, timedelta

username = "02-2324-12504"
password = "EVANGELISTA"

while True:
    user = input("Enter username: ")
    pw = input("Enter password: ")
    if user == username and pw == password:
        print("Login successful!")
        break
    else:
        print("Invalid username or password. Try again.\n")

books = []

while True:
    print("\n=== Library Borrowing and Returning System ===")
    print("1. Borrow Book")
    print("2. Return Book")
    choice = input("type 'exit' to quit: ").strip().lower()

    if choice == "1":
        name = input("Your name: ")
        title = input("Book title: ")
        aisle = input("Aisle: ")
        row = input("Row: ")
        days = int(input("Days to borrow: "))
        due = datetime.now() + timedelta(days=days)

        books.append({
            "name": name,
            "title": title,
            "aisle": aisle,
            "row": row,
            "due": due
        })

        print("\n--- Borrow Receipt ---")
        print(f"Name     : {name}")
        print(f"Book     : {title}")
        print(f"Aisle    : {aisle} | Row: {row}")
        print(f"Return by: {due.strftime('%Y-%m-%d')}")
        print("----------------------")

    elif choice == "2":
        title = input("Book title to return: ")
        found = False

        for b in books:
            if b["title"].lower() == title.lower():
                print("\n--- Return Receipt ---")
                print(f"Returned '{b['title']}'")
                print(f"Return Location: Aisle {b['aisle']} | Row {b['row']}")
                print("----------------------")
                books.remove(b)
                found = True
                break

        if not found:
            print("Book not found!")

    elif choice == "exit":
        print("Thank you for Visiting!\nGOODBYE!")
        break
