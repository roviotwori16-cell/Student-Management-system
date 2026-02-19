import java.util.Scanner;
 
abstract class Person {
    protected String name;

    public Person(String name) {
        this.name = name;
    }

    public abstract void displayDetails();
}

class Course {
    private String courseName;

    public Course(String courseName) {
        this.courseName = courseName;
    }

    public String getCourseName() {
        return courseName;
    }
}

class Student extends Person {

    private int studentId;
    private int marks;
    private Course course;

    public Student(int studentId, String name, int marks, Course course) {
        super(name);
        this.studentId = studentId;
        this.marks = marks;
        this.course = course;
    }

    // Grade calculation
    public String calculateGrade() {
        if (marks >= 70)
            return "A";
        else if (marks >= 60)
            return "B";
        else if (marks >= 50)
            return "C";
        else
            return "Fail";
    }

    // Overriding method
    @Override
    public void displayDetails() {
        System.out.println("\n--- Student Details ---");
        System.out.println("ID: " + studentId);
        System.out.println("Name: " + name);
        System.out.println("Course: " + course.getCourseName());
        System.out.println("Marks: " + marks);
        System.out.println("Grade: " + calculateGrade());  // ← This prints grade
    }
}

public class StudentManagementSystem {
    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        System.out.print("Enter Student ID: ");
        int id = input.nextInt();
        input.nextLine();

        System.out.print("Enter Name: ");
        String name = input.nextLine();

        System.out.print("Enter Course Name: ");
        String courseName = input.nextLine();

        System.out.print("Enter Marks: ");
        int marks = input.nextInt();

        Course course = new Course(courseName);
        Student student = new Student(id, name, marks, course);

        student.displayDetails();   // ← MUST call this

        input.close();
    }
}
