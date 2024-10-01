# Sudent-management-system

#include <iostream>
#include <vector>
#include <string>

using namespace std;

struct Student {

    int id;
    string name;
    int age;
};

vector<Student> students;

void insertStudent() {
    Student newStudent;
    cout << "Enter Student ID: ";
    cin >> newStudent.id;
    cout << "Enter Student Name: ";
    cin.ignore(); // To ignore the newline character left by previous input
    getline(cin, newStudent.name);
    cout << "Enter Student Age: ";
    cin >> newStudent.age;
    students.push_back(newStudent);
    cout << "Student record inserted successfully!" << endl;
}
void updateStudent() {
    int id;
    cout << "Enter Student ID to update: ";
    cin >> id;
    for (auto &student : students) {
        if (student.id == id) {
            cout << "Enter new name: ";
            cin.ignore();
            getline(cin, student.name);
            cout << "Enter new age: ";
            cin >> student.age;
            cout << "Student record updated successfully!" << endl;
            return;
        }
    }
    cout << "Student ID not found!" << endl;
}

void displayStudents() {
    cout << "Student Records:" << endl;
    for (const auto &student : students) {
        cout << "ID: " << student.id << ", Name: " << student.name << ", Age: " << student.age << endl;
    }
}

int main() {
    int choice;
    while (true) {
        cout << "1. Insert Student\n2. Update Student\n3. Display Students\n4. Exit\nEnter your choice: ";
        cin >> choice;
        switch (choice) {
            case 1:
                insertStudent();
                break;
            case 2:
                updateStudent();
                break;
            case 3:
                displayStudents();
                break;
            case 4:
                return 0;
            default:
                cout << "Invalid choice! Please try again." << endl;
        }
    }
    return 0;
}
