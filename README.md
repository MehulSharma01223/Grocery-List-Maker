# Grocery-List-Maker
A beginner-friendly Python program that helps users create and manage their personal grocery list. This project demonstrates the use of if-else conditions, loops, lists, sets, tuples, and dictionaries in a practical and fun way.
# =======================================
#        GROCERY LIST MAKER PROJECT
# =======================================

# 1. TUPLE → Available grocery categories
CATEGORIES = (
    "Fruits",
    "Vegetables",
    "Dairy",
    "Snacks",
    "Beverages"
)

# 2. DICTIONARY → Suggested items for each category
SUGGESTIONS = {
    "Fruits": ["Apples", "Bananas", "Grapes"],
    "Vegetables": ["Potatoes", "Tomatoes", "Carrots"],
    "Dairy": ["Milk", "Cheese", "Butter"],
    "Snacks": ["Chips", "Biscuits", "Chocolate"],
    "Beverages": ["Juice", "Tea", "Coffee"]
}

# 3. LIST → User’s grocery list
grocery_list = []

# 4. SET → To avoid duplicate items
added_items = set()

print("\n===== GROCERY LIST MAKER =====")

while True:
    print("\n--- GROCERY CATEGORIES ---")
    for i, cat in enumerate(CATEGORIES):
        print(f"{i+1}. {cat}")

    print("6. View List")
    print("7. Finish")

    choice = input("\nChoose a category number: ")

    # --- IF-ELSE for choosing categories ---
    if choice == "7":
        break

    elif choice == "6":
        print("\n----- YOUR GROCERY LIST -----")
        if not grocery_list:
            print("Your list is empty!")
        else:
            for idx, item in enumerate(grocery_list, 1):
                print(f"{idx}. {item}")
        continue

    elif choice in ["1", "2", "3", "4", "5"]:
        choice = int(choice) - 1
        category = CATEGORIES[choice]

        print(f"\n--- {category.upper()} ---")
        print("Suggestions:", ", ".join(SUGGESTIONS[category]))

        item = input("Enter the item you want to add: ").strip().title()

        # SET → Prevent duplicates
        if item in added_items:
            print("This item is already in your list!")
        else:
            grocery_list.append(item)
            added_items.add(item)
            print(f"Added: {item}")

    else:
        print("Invalid choice! Try again.")

# ======= FINAL LIST =======
print("\n=============================")
print("       YOUR FINAL LIST       ")
print("=============================")

if not grocery_list:
    print("Your list is empty!")
else:
    # Loop → Show items
    for i, item in enumerate(grocery_list, 1):
        print(f"{i}. {item}")

print("\nHappy Shopping! 🛒")
