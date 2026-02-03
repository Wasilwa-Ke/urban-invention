Class:1.Books
      2.Users
      3.library
.The book class handles book details and availability.
The user class stores user information.
Library class manages collection of books and users and also provides methods to borrow and return books.



#include <iostream>
#include <vector>
#include <string>
using namespace std;

class Book {
    int bookID;
    string title, author;
    bool isAvailable;
public:
    Book(int id, string t, string a) : bookID(id), title(t), author(a), isAvailable(true) {}
    void displayBook() {
        cout << "ID: " << bookID << " | Title: " << title << " | Author: " << author
             << " | Available: " << (isAvailable ? "Yes" : "No") << endl;
    }
    bool getAvailability() { return isAvailable; }
    string getTitle() { return title; }
    void borrowBook() { isAvailable = false; }
    void returnBook() { isAvailable = true; }
};

class User {
    int userID;
    string name;
public:
    User(int id, string n) : userID(id), name(n) {}
    void displayUser() { cout << "User ID: " << userID << " | Name: " << name << endl; }
};

class Library {
    vector<Book> books;
    vector<User> users;
public:
    void addBook(Book b) { books.push_back(b); }
    void addUser(User u) { users.push_back(u); }
    void displayAllBooks() {
        cout << "\n--- Library Books ---\n";
        for (auto &b : books) b.displayBook();
    }
    void searchBook(string title) {
        for (auto &b : books) {
            if (b.getTitle() == title) {
                cout << "Book found:\n";
                b.displayBook();
                return;
            }
        }
        cout << "Book not found.\n";
    }
};

int main() {
    Library lib;
    lib.addBook(Book(1, "C++ Programming", "Bjarne Stroustrup"));
    lib.addBook(Book(2, "Clean Code", "Robert C. Martin"));
    lib.addUser(User(101, "Ian Nyukuri"));

    lib.displayAllBooks();
    lib.searchBook("C++ Programming");

    return 0;
}




