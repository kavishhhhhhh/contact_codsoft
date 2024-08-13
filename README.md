# contact_codsoft
contacts = {}

def display_menu():
    print("\nContact Book Menu:")
    print("1. Add a New Contact")
    print("2. View All Contacts")
    print("3. Search for a Contact")
    print("4. Update a Contact")
    print("5. Delete a Contact")
    print("6. Exit")

def add_contact():
    name = input("\nEnter Name: ").strip()
    phone = input("Enter Phone Number: ").strip()
    email = input("Enter Email: ").strip()
    address = input("Enter Address: ").strip()

    if name in contacts:
        print("A contact with this name already exists. Use update to modify the contact.")
        return

    contacts[name] = {"phone": phone, "email": email, "address": address}
    print(f"Contact '{name}' added successfully.")

def view_contacts():
    if not contacts:
        print("\nNo contacts found.")
        return

    print("\nContact List:")
    for name, details in contacts.items():
        print(f"Name: {name}, Phone: {details['phone']}, Email: {details['email']}, Address: {details['address']}")

def search_contact():
    search_term = input("\nEnter the name or phone number to search: ").strip()

    found_contacts = {name: details for name, details in contacts.items() if search_term in name or search_term in details['phone']}

    if not found_contacts:
        print("No contacts found.")
    else:
        print("\nSearch Results:")
        for name, details in found_contacts.items():
            print(f"Name: {name}, Phone: {details['phone']}, Email: {details['email']}, Address: {details['address']}")

def update_contact():
    name = input("\nEnter the name of the contact to update: ").strip()

    if name in contacts:
        print(f"Current details for '{name}': Phone: {contacts[name]['phone']}, Email: {contacts[name]['email']}, Address: {contacts[name]['address']}")
        phone = input("Enter new Phone Number (leave blank to keep current): ").strip()
        email = input("Enter new Email (leave blank to keep current): ").strip()
        address = input("Enter new Address (leave blank to keep current): ").strip()

        if phone:
            contacts[name]['phone'] = phone
        if email:
            contacts[name]['email'] = email
        if address:
            contacts[name]['address'] = address

        print(f"Contact '{name}' updated successfully.")
    else:
        print("Contact not found.")

def delete_contact():
    name = input("\nEnter the name of the contact to delete: ").strip()

    if name in contacts:
        del contacts[name]
        print(f"Contact '{name}' deleted successfully.")
    else:
        print("Contact not found.")

def contact_book_app():
    while True:
        display_menu()
        choice = input("\nEnter your choice (1-6): ").strip()

        if choice == '1':
            add_contact()
        elif choice == '2':
            view_contacts()
        elif choice == '3':
            search_contact()
        elif choice == '4':
            update_contact()
        elif choice == '5':
            delete_contact()
        elif choice == '6':
            print("Exiting the Contact Book application. Goodbye!")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 6.")

contact_book_app()
