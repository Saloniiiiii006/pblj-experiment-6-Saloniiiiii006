[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/pAwhWXY5)
import java.util.*;
import java.util.stream.Collectors;

class Student {
    String name;
    double marks;

    public Student(String name, double marks) {
        this.name = name;
        this.marks = marks;
    }

    public String getName() {
        return name;
    }

    public double getMarks() {
        return marks;
    }
}

public class StudentFilter {
    public static void main(String[] args) {
        
        List<Student> students = Arrays.asList(
                new Student("Alice", 85.5),
                new Student("Bob", 72.0),
                new Student("Charlie", 90.2),
                new Student("David", 65.4),
                new Student("Emma", 78.9)
        );

       
        List<String> topStudents = students.stream()
                .filter(s -> s.getMarks() > 75) // Filter students scoring above 75%
                .sorted(Comparator.comparingDouble(Student::getMarks).reversed()) // Sort by marks in descending order
                .map(Student::getName) // Extract names
                .collect(Collectors.toList()); // Collect to list

        
        System.out.println("Students scoring above 75% (sorted by marks): " + topStudents);
    }
}
