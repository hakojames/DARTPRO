// Interface for classes that can print their information
abstract class Printable {
  void printInfo();
}

// Base class for Person
class Person {
  String name;

  Person(this.name);

  void introduce() {
    print("Hello, my name is $name.");
  }
}

// Student class inherits from Person and implements Printable
class Student extends Person implements Printable {
  int gradeLevel;
  List<Course> enrolledCourses;

  Student(String name, this.gradeLevel, {String filePath}) : super(name) {
    enrolledCourses = [];
    if (filePath != null) {
      // Read student data from file (implementation omitted for brevity)
      // Populate student information from file data
    }
  }

  @override
  void printInfo() {
    super.introduce();
    print("Grade Level: $gradeLevel");
    print("Enrolled Courses:");
    for (var course in enrolledCourses) {
      course.printInfo();
    }
  }

  // Override inherited method with student-specific details
  @override
  void introduce() {
    super.introduce();
    print("I am a student in grade $gradeLevel.");
  }
}

// Course class implements Printable
class Course {
  String name;
  String instructor;

  Course(this.name, this.instructor);

  @override
  void printInfo() {
    print("Course Name: $name");
    print("Instructor: $instructor");
  }
}

// Function to print information of all students in a list
void printAllStudents(List<Student> students) {
  for (var student in students) {
    student.printInfo();
    print("------------------");
  }
}

void main() {
  // Create some students
  var student1 = Student("Alice", 12);
  var student2 = Student("Bob", 10, filePath: "data/student2.txt");

  // Create some courses
  var course1 = Course("Math", "Mr. Jones");
  var course2 = Course("English", "Ms. Smith");

  // Enroll students in courses (example)
  student1.enrolledCourses.add(course1);
  student2.enrolledCourses.add(course2);

  // List of students
  var students = [student1, student2];

  // Print information of all students
  printAllStudents(students);
