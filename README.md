# STUDENT-MANAGEMENT-SYSTEM
Introduction
This project is a simple Student Management System implemented in Python. It provides basic functionalities for managing student records, including adding, updating, deleting, and viewing student information. The system uses a text-based menu for user interaction, making it easy to use and understand.
# student.py
class Student:
    def __init__(self, id, name, age, major):
        self.id = id
        self.name = name
        self.age = age
        self.major = major

    def update_student(self, name=None, age=None, major=None):
        if name:
            self.name = name
        if age:
            self.age = age
        if major:
            self.major = major

    def __str__(self):
        return f"ID: {self.id}, Name: {self.name}, Age: {self.age}, Major: {self.major}"

# student_database.py
class StudentDatabase:
    def __init__(self):
        self.students = {}

    def add_student(self, student):
        if student.id in self.students:
            print(f"Student with ID {student.id} already exists.")
        else:
            self.students[student.id] = student
            print(f"Student {student.name} added successfully.")

    def remove_student(self, student_id):
        if student_id in self.students:
            del self.students[student_id]
            print(f"Student with ID {student_id} removed successfully.")
        else:
            print(f"No student found with ID {student_id}.")

    def update_student(self, student_id, name=None, age=None, major=None):
        student = self.students.get(student_id)
        if student:
            student.update_student(name, age, major)
            print(f"Student with ID {student_id} updated successfully.")
        else:
            print(f"No student found with ID {student_id}.")

    def get_student(self, student_id):
        return self.students.get(student_id, None)

    def display_all_students(self):
        for student in self.students.values():
            print(student)

# main.py
from student import Student
from student_database import StudentDatabase

class StudentManagementSystem:
    def __init__(self):
        self.database = StudentDatabase()

    def add_new_student(self):
        id = int(input("Enter student ID: "))
        name = input("Enter student name: ")
        age = int(input("Enter student age: "))
        major = input("Enter student major: ")
        student = Student(id, name, age, major)
        self.database.add_student(student)

    def delete_student(self):
        student_id = int(input("Enter student ID to delete: "))
        self.database.remove_student(student_id)

    def update_student_info(self):
        student_id = int(input("Enter student ID to update: "))
        name = input("Enter new name (leave blank to keep current): ")
        age = input("Enter new age (leave blank to keep current): ")
        major = input("Enter new major (leave blank to keep current): ")
        self.database.update_student(
            student_id,
            name=name if name else None,
            age=int(age) if age else None,
            major=major if major else None
        )

    def show_all_students(self):
        self.database.display_all_students()

    def run(self):
        while True:
            print("\n1. Add Student")
            print("2. Delete Student")
            print("3. Update Student Information")
            print("4. Show All Students")
            print("5. Exit")

            choice = input("Enter your choice: ")

            if choice == '1':
                self.add_new_student()
            elif choice == '2':
                self.delete_student()
            elif choice == '3':
                self.update_student_info()
            elif choice == '4':
                self.show_all_students()
            elif choice == '5':
                print("Exiting...")
                break
            else:
                print("Invalid choice. Please enter a number between 1 and 5.")

# To run the system
if __name__ == "__main__":
    sms = StudentManagementSystem()
    sms.run()

    

    # Student Management System

## Overview
This is a simple Student Management System designed to manage student information. The system allows administrators to add, delete, update, and view student records. The system is built using Python and follows key software design principles such as SOLID, DRY, KISS, and YAGNI.

## How to Run
1. Clone the repository to your local machine.
2. Navigate to the project directory.
3. Run the `main.py` file using Python:
    ```
    python main.py
    ```

## Features
- Add a new student.
- Delete an existing student.
- Update student information.
- View all students.

## Design Principles
The system was refactored to adhere to the following principles:

- **SOLID Principles**: The code is modular, with each class having a single responsibility, making it easy to maintain and extend.
- **DRY (Don't Repeat Yourself)**: The code avoids duplication by centralizing common functionalities.
- **KISS (Keep It Simple, Stupid)**: The design is simple and easy to understand, avoiding unnecessary complexity.
- **YAGNI (You Ain't Gonna Need It)**: The code includes only necessary features, preventing over-engineering.

## Future Improvements
- Add more user-friendly error handling.
- Implement persistent storage for student data.
- Develop a graphical user interface (GUI) for better user experience.

