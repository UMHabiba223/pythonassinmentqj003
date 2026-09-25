class Student:

    def __init__(self, name, student_id, email, age, department):
        self.name = name
        self.student_id = student_id
        self.__email = email
        self.age = age
        self.department = department
        self.__marks = []

    def display_info(self):
        print("\nStudent Information\n")
        print("Name:", self.name)
        print("Student ID:", self.student_id)
        print("Email:", self.__email)
        print("Age:", self.age)
        print("Department:", self.department)
        print("Student Type:", self.get_student_type())

    def calculate_result(self, *marks):
        self.__marks = marks

        if len(marks) == 0:
            print("No marks entered.")
            return

        total = sum(marks)
        average = total / len(marks)

        print("Total Marks:", total)
        print("Average Marks:", average)

        if average >= 80:
            print("Grade: A+")
        elif average >= 70:
            print("Grade: A")
        elif average >= 60:
            print("Grade: B")
        elif average >= 50:
            print("Grade: C")
        elif average >= 40:
            print("Grade: D")
        else:
            print("Grade: F")

    def get_student_type(self):
        return "Student"

    def get_email(self):
        return self.__email


class UndergraduateStudent(Student):

    def __init__(self, name, student_id, email, age, department, semester):
        super().__init__(name, student_id, email, age, department)
        self.semester = semester

    def get_student_type(self):
        return "Undergraduate Student"

    def display_info(self):
        super().display_info()
        print("Semester:", self.semester)


class GraduateStudent(Student):

    def __init__(self, name, student_id, email, age, department, research_topic):
        super().__init__(name, student_id, email, age, department)
        self.research_topic = research_topic

    def get_student_type(self):
        return "Graduate Student"

    def display_info(self):
        super().display_info()
        print("Research Topic:", self.research_topic)


student1 = UndergraduateStudent(
    "Richi",
    "12345",
    "richa022@example.com",
    21,
    "CSE",
    5
)

student2 = GraduateStudent(
    "Fatema",
    "54321",
    "Fatema86654@example.com",
    24,
    "CSE",
    "Artificial Intelligence"
)


student1.display_info()
student2.display_info()

print("\nUndergraduate Result\n")
student1.calculate_result(85, 78, 90, 88)

print("\nGraduate Result\n")
student2.calculate_result(75, 82, 79)

print("\nPolymorphism\n")

students = [student1, student2]

for student in students:
    print(student.get_student_type())
