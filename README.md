# codeAlpha_student-grade-tracker

import java.util.ArrayList;
import java.util.Scanner;

class Student {
    String name;
    double marks;

    Student(String name, double marks) {
        this.name = name;
        this.marks = marks;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<Student> students = new ArrayList<>();

        System.out.print("Enter number of students: ");
        int n = sc.nextInt();
        sc.nextLine();

        if (n <= 0) {
            System.out.println("Number of students must be positive.");
            sc.close();
            return;
        }

        // Input student details
        for (int i = 0; i < n; i++) {
            System.out.println("\nStudent " + (i + 1));

            System.out.print("Enter student name: ");
            String name = sc.nextLine();

            double marks;
            while (true) {
                System.out.print("Enter marks (0-100): ");
                marks = sc.nextDouble();
                sc.nextLine();

                if (marks >= 0 && marks <= 100) {
                    break;
                }
                System.out.println("Invalid marks! Try again.");
            }

            students.add(new Student(name, marks));
        }

        // Calculate statistics
        double total = 0;
        double highest = students.get(0).marks;
        double lowest = students.get(0).marks;

        for (Student s : students) {
            total += s.marks;

            if (s.marks > highest) {
                highest = s.marks;
            }

            if (s.marks < lowest) {
                lowest = s.marks;
            }
        }

        double average = total / students.size();

        // Display summary report
        System.out.println("\n===== STUDENT GRADE REPORT =====");
        System.out.printf("%-20s %s%n", "Student Name", "Marks");
        System.out.println("--------------------------------");

        for (Student s : students) {
            System.out.printf("%-20s %.2f%n", s.name, s.marks);
        }

        System.out.println("--------------------------------");
        System.out.printf("Average Marks : %.2f%n", average);
        System.out.printf("Highest Marks : %.2f%n", highest);
        System.out.printf("Lowest Marks  : %.2f%n", lowest);

        sc.close();
    }
}
