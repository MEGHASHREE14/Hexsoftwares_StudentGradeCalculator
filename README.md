import java.util.ArrayList;
import java.util.Scanner;

class Student {
    private String name;
    private String studentId;
    private ArrayList<Integer> grades;

    
    public Student(String name, String studentId) {
        this.name = name;
        this.studentId = studentId;
        this.grades = new ArrayList<>();
    }

   
    public void addGrade(int grade) {
        grades.add(grade);
    }

    
    public void displayGrades() {
        System.out.print("Grades: ");
        for (int grade : grades) {
            System.out.print(grade + " ");
        }
        System.out.println();
    }

   
    public double calculateAverage() {
        if (grades.isEmpty()) return 0;
        int sum = 0;
        for (int grade : grades) {
            sum += grade;
        }
        return (double) sum / grades.size();
    }

    
    public boolean hasPassed() {
        return calculateAverage() >= 50;
    }

    
    public String getName() {
        return name;
    }

    public String getStudentId() {
        return studentId;
    }
}

public class StudentGradeCalculator {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<Student> students = new ArrayList<>();

        System.out.print("Enter number of students: ");
        int numStudents = sc.nextInt();
        sc.nextLine(); 

        
        for (int i = 0; i < numStudents; i++) {
            System.out.println("\nEnter details for Student " + (i + 1));
            System.out.print("Name: ");
            String name = sc.nextLine();
            System.out.print("Student ID: ");
            String id = sc.nextLine();

            Student student = new Student(name, id);

            System.out.print("Enter number of grades: ");
            int numGrades = sc.nextInt();

            for (int j = 0; j < numGrades; j++) {
                System.out.print("Enter grade " + (j + 1) + ": ");
                int grade = sc.nextInt();
                student.addGrade(grade);
            }
            sc.nextLine(); 
            students.add(student);
        }

     
        double totalClassAverage = 0;
        System.out.println("\n--- Student Results ---");
        for (Student student : students) {
            System.out.println("Name: " + student.getName() + " | ID: " + student.getStudentId());
            student.displayGrades();
            double avg = student.calculateAverage();
            System.out.printf("Average: %.2f\n", avg);
            System.out.println("Result: " + (student.hasPassed() ? "Passed" : "Failed"));
            System.out.println("------------------------");
            totalClassAverage += avg;
        }

       
        if (!students.isEmpty()) {
            double classAverage = totalClassAverage / students.size();
            System.out.printf("\nClass Average: %.2f\n", classAverage);
        }

        sc.close();
    }
}
# Hexsoftwares_StudentGradeCalculator
