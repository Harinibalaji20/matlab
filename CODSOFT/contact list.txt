def clear_screen():
    print("\n" * 100) 
def get_contact_details():
    person_name = input("Enter person name: ")
    phone_number = input("Enter phone number: ")
    address = input("Enter address: ")
    email = input("Enter email: ")
    return {"person_name": person_name, "phone_number": phone_number, "address": address, "email": email}
def add_contact(contacts):
    print("\n~~~ Add New Contact ~~~")
    contact = get_contact_details()
    contacts.append(contact)
    print(" wow!!Contact added successfully!")
def view_contact_list(contacts):
    print("\n~~~ Contact List ~~~")
    if not contacts:
        print(" sorry!No contacts available.")
        return
    for i, contact in enumerate(contacts):
        print(f"{i+1}. person Name: {contact['person_name']}, Phone: {contact['phone_number']}")
def update_contact(contacts):
    print("\n~~~ Update Contact ~~~")
    if not contacts:
        print("Sorry!No contacts available to update.")
        return
    view_contact_list(contacts)
    try:
        contact_index = int(input("Enter the number of the contact to update: ")) - 1
        if 0 <= contact_index < len(contacts):
            print(f"Current details for {contacts[contact_index]['person_name']}:")
            print(f"Phone Number: {contacts[contact_index]['phone_number']}")
            print(f"Address: {contacts[contact_index]['address']}")
            print(f"Email: {contacts[contact_index]['email']}")

            print("Enter new details (leave blank to keep current value):")
            new_person_name = input(f"New person Name ({contacts[contact_index]['person_name']}): ")
            new_phone_number = input(f"New Phone Number ({contacts[contact_index]['phone_number']}): ")
            new_email = input(f"New Email ({contacts[contact_index]['email']}): ")
            new_address = input(f"New Address ({contacts[contact_index]['address']}): ")

            if new_person_name:
                contacts[contact_index]['person_name'] = new_person_name
            if new_phone_number:
                contacts[contact_index]['phone_number'] = new_phone_number
            if new_email:
                contacts[contact_index]['email'] = new_email
            if new_address:
                contacts[contact_index]['address'] = new_address

            print("Contact updated successfully!")
        else:
            print("Invalid contact number.")
    except ValueError:
        print("Invalid input. Please enter a number.")
def search_contact(contacts):
    print("\n~~~ Search Contact ~~~")
    if not contacts:
        print("Sorry!No contacts available to search.")
        return
    search_term = input("Enter person name or phone number to search: ")
    found_contacts = []
    for contact in contacts:
        if search_term in contact['person_name'] or search_term in contact['phone_number']:
            found_contacts.append(contact)
    if not found_contacts:
        print(" Sorry!No matching contacts found.")
    else:
        print("\n~~~ Search Results ~~~")
        for contact in found_contacts:
            print(f"person Name: {contact['person_name']}")
            print(f"Phone Number: {contact['phone_number']}")
            print(f"Address: {contact['address']}")
            print(f"Email: {contact['email']}")

def delete_contact(contacts):
    print("\n~~~ Delete Contact ~~~")
    if not contacts:
        print(" sorry!No contacts available to delete.")
        return
    view_contact_list(contacts)
    try:
        contact_index = int(input("Enter the number of the contact to delete: ")) - 1
        if 0 <= contact_index < len(contacts):
            deleted_contact = contacts.pop(contact_index)
            print(f"Contact '{deleted_contact['person_name']}' deleted successfully!")
        else:
            print("Invalid contact number.")
    except ValueError:
        print("Invalid input. Please enter a number.")

def main():
    contacts = []  
    while True:
        clear_screen()
        print("\n~~~ Contact details ~~~")
        print("1. Add Contact")
        print("2. View Contact List")
        print("3. Update Contact")
        print("4. Search Contact")
        print("5. Delete Contact")
        print("6. Exit")
        choice = input("Enter your choice (1-6): ")
        if choice == '1':
            add_contact(contacts)
        elif choice == '2':
            view_contact_list(contacts)
        elif choice == '3':
            update_contact(contacts)
        elif choice == '4':
            search_contact(contacts)
        elif choice == '5':
            delete_contact(contacts)
        elif choice == '6':
            print("Exiting Contact details. Goodbye!")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 6.")
        input("\nPress Enter to continue...")
if __name__ == "__main__":
    main()
