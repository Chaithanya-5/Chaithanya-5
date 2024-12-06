lass Book:
    def __init__(self, title, author, isbn):
        self.title = title
        self.author = author
        self.isbn = isbn
        self.checked_out = False

    def __str__(self):
        return f"Title: {self.title}, Author: {self.author}, ISBN: {self.isbn}, Checked Out: {self.checked_out}"


class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)
        print(f"Added: {book}")

    def remove_book(self, isbn):
        for book in self.books:
            if book.isbn == isbn:
                self.books.remove(book)
                print(f"Removed: {book}")
                return
        print("Book not found.")

    def list_books(self):
        if not self.books:
            print("No books in library.")
        for book in self.books:
            print(book)

    def check_out(self, isbn):
        for book in self.books:
            if book.isbn == isbn:
                if not book.checked_out:
                    book.checked_out = True
                    print(f"Checked out: {book}")
                else:
                    print("Book is already checked out.")
                return
        print("Book not found.")

    def return_book(self, isbn):
        for book in self.books:
            if book.isbn == isbn:
                if book.checked_out:
                    book.checked_out = False
                    print(f"Returned: {book}")
                else:
                    print("Book was not checked out.")
                return
        print("Book not found.")


def main():
    library = Library()

    while True:
        print("\nLibrary Management System")
        print("1. Add Book")
        print("2. Remove Book")
        print("3. List Books")
        print("4. Check Out Book")
        print("5. Return Book")
        print("6. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            title = input("Enter book title: ")
            author = input("Enter book author: ")
            isbn = input("Enter book ISBN: ")
            book = Book(title, author, isbn)
            library.add_book(book)

        elif choice == "2":
            isbn = input("Enter book ISBN to remove: ")
            library.remove_book(isbn)

        elif choice == "3":
            library.list_books()

        elif choice == "4":
            isbn = input("Enter book ISBN to check out: ")
            library.check_out(isbn)

        elif choice == "5":
            isbn = input("Enter book ISBN to return: ")
            library.return_book(isbn)

        elif choice == "6":
            break

        else:
            print("Invalid choice. Please select a valid option.")

if __name__ == "__main__":
    main()
