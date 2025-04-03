Python YAML Use Case
====================

Overview
--------

This project demonstrates how to work with YAML files in Python using the `PyYAML` library. It reads student information from a YAML file and provides functionalities to display and filter students based on GPA.

Prerequisites
-------------

Make sure you have Python installed. You also need the `PyYAML` package. Install it using:

```
pip install pyyaml

```

YAML File Structure
-------------------

Create a `students.yaml` file with the following content:

```
students:
  - name: Alice
    age: 21
    major: Computer Science
    gpa: 3.8
  - name: Bob
    age: 22
    major: Mathematics
    gpa: 3.5
  - name: Charlie
    age: 20
    major: Physics
    gpa: 3.9
  - name: David
    age: 23
    major: Chemistry
    gpa: 3.2
  - name: Eva
    age: 21
    major: Computer Science
    gpa: 3.7

```

Python Script
-------------

Create an `app.py` file with the following code:

```
import yaml

def load_data(file_path):
    with open(file_path, 'r') as file:
        data = yaml.safe_load(file)
    return data

def display_students(students):
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]
    print(f"\nStudents with GPA >= {min_gpa}:")
    if filtered_students:
        for student in filtered_students:
            print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    else:
        print("No students found.")

def main():
    data = load_data('students.yaml')
    students = data['students']
    display_students(students)
    min_gpa = float(input("\nEnter minimum GPA to filter students: "))
    filter_students_by_gpa(students, min_gpa)

if __name__ == "__main__":
    main()

```

Running the Application
-----------------------

Ensure that `app.py` and `students.yaml` are in the same directory, then run:

```
python app.py

```

### Expected Output

```
All Students:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Bob, Age: 22, Major: Mathematics, GPA: 3.5
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: David, Age: 23, Major: Chemistry, GPA: 3.2
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7

Enter minimum GPA to filter students: 3.6

Students with GPA >= 3.6:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7

```

Conclusion
----------

This application serves as a basic example of handling YAML files in Python. You can extend it by adding sorting, updating student information, or writing back to the YAML file.