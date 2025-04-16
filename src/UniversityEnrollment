import java.util.*;

class CourseFullException extends Exception {
    public CourseFullException(String message) {
        super(message);
    }
}

class PrerequisiteNotMetException extends Exception {
    public PrerequisiteNotMetException(String message) {
        super(message);
    }
}

class Course {
    private String name;
    private int capacity;
    private List<String> prerequisites;
    private List<String> enrolledStudents;

    public Course(String name, int capacity, List<String> prerequisites) {
        this.name = name;
        this.capacity = capacity;
        this.prerequisites = prerequisites;
        this.enrolledStudents = new ArrayList<>();
    }

    public String getName() {
        return name;
    }

    public boolean hasPrerequisite(String course) {
        return prerequisites.contains(course);
    }

    public void enrollStudent(String student, List<String> completedCourses) throws CourseFullException, PrerequisiteNotMetException {
        if (enrolledStudents.size() >= capacity) {
            throw new CourseFullException("Course is full: " + name);
        }
        for (String prerequisite : prerequisites) {
            if (!completedCourses.contains(prerequisite)) {
                throw new PrerequisiteNotMetException("Complete " + prerequisite + " before enrolling in " + name + ".");
            }
        }
        enrolledStudents.add(student);
        System.out.println("Enrolled successfully in " + name);
    }
}

public class UniversityEnrollment {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        Map<String, Course> courses = new HashMap<>();
        courses.put("Advanced Java", new Course("Advanced Java", 2, Arrays.asList("Core Java")));
        courses.put("Core Java", new Course("Core Java", 2, Collections.emptyList()));
        
        System.out.print("Enroll in Course: ");
        String courseName = scanner.nextLine();
        
        System.out.print("Prerequisite: ");
        String prerequisite = scanner.nextLine();

        scanner.close();
        
        List<String> completedCourses = new ArrayList<>();
        if (!prerequisite.isEmpty()) {
            completedCourses.add(prerequisite);
        }
        
        if (!courses.containsKey(courseName)) {
            System.out.println("Course not found.");
            return;
        }
        
        try {
            courses.get(courseName).enrollStudent("Student", completedCourses);
        } catch (CourseFullException | PrerequisiteNotMetException e) {
            System.out.println("Error: " + e.getClass().getSimpleName() + " - " + e.getMessage());
        }
        
        scanner.close();
    }
}
