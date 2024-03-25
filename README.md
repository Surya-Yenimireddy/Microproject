# Microproject
import shelve

def add_data(db):
    key = input("Enter a key: ")
    value = input("Enter a value: ")
    db[key] = value
    print(f"Added: {key} -> {value}")

def modify_data(db):
    key = input("Enter the key to modify: ")
    if key in db:
        new_value = input("Enter the new value: ")
        db[key] = new_value
        print(f"Modified: {key} -> {new_value}")
    else:
        print(f"Key '{key}' not found in the database.")

def delete_data(db):
    key = input("Enter the key to delete: ")
    if key in db:
        del db[key]
        print(f"Deleted: {key}")
    else:
        print(f"Key '{key}' not found in the database.")

def list_keys(db):
    keys = list(db.keys())
    print("Available keys in the database:")
    for key in keys:
        print(key)

def main():
    with shelve.open('mydatabase.db', writeback=True) as db:
        while True:
            print("\nOptions:")
            print("1. Add data")
            print("2. Modify data")
            print("3. Delete data")
            print("4. List keys")
            print("5. Exit")
            choice = input("Enter your choice (1/2/3/4/5): ")

            if choice == '1':
                add_data(db)
            elif choice == '2':
                modify_data(db)
            elif choice == '3':
                delete_data(db)
            elif choice == '4':
                list_keys(db)
            elif choice == '5':
                break
            else:
                print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
