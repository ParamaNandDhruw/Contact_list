# Contact_list
the simple basic python code for contact list

import json

FILE = "contact_list.json"


def load_contacts():
    try:
        with open(FILE, "r") as f:
            return json.load(f)

    except:
        return {"contacts": []}


def save_contact(data):
    with open(FILE, "w") as f:
        json.dump(data, f, indent=4)


def add_contact():

    name = input("Enter name: ")
    number = input("Enter number: ")

    data = load_contacts()

    contact = {
        "name": name,
        "number": number
    }

    data["contacts"].append(contact)

    save_contact(data)

    print("Contact saved!")


def show_contacts():

    data = load_contacts()

    if not data["contacts"]:
        print("No contacts found.")
        return

    for i, contact in enumerate(data["contacts"], 1):
        print(i, contact["name"], "-", contact["number"])

def search_list():
    data = load_contacts()
    search = input("name")
    for  contact in data["contacts"]:
            if contact["name"] == search:
                print(contact)
            
            if not data["contacts"]:
                print("data not ")
                return 
                
def delete_cotact():
    data = load_contacts()
    
    choice = input("Enter name:")
    
    for contact in data["contacts"]:
        if data["contacts"] == choice:
            data["contacts"].pop(choice -1)
            
    save_contact(data)
    print("Contact deleted.")                               
while True:

    print("\n1. Add Contact")
    print("2. Show Contacts")
    print("3. Search Contacts")
    print("4. delete contact")

    choice = input("Enter choice: ")

    if choice == "1":
        add_contact()

    elif choice == "2":
        show_contacts()

    elif choice == "3":
        search_list()
    
    elif choice == "4":
        delete_cotact()
        
    else:
        print("Exiting.....")
        break
