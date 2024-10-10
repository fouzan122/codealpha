# codealpha
import java.util.ArrayList;
import java.util.Scanner;

public class StudentGrades {

    public static void main(String[] args) {
        ArrayList<Double> grades = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);
        String input;

        System.out.println("Enter student grades (type 'done' to finish):");

        // Input loop
        while (true) {
            input = scanner.nextLine();

            if (input.equalsIgnoreCase("done")) {
                break;
            }

            try {
                double grade = Double.parseDouble(input);
                grades.add(grade);
            } catch (NumberFormatException e) {
                System.out.println("Please enter a valid grade or 'done' to finish.");
            }
        }

        // Compute average, highest, and lowest scores
        if (!grades.isEmpty()) {
            double sum = 0;
            double highest = grades.get(0);
            double lowest = grades.get(0);

            for (double grade : grades) {
                sum += grade;
                if (grade > highest) {
                    highest = grade;
                }
                if (grade < lowest) {
                    lowest = grade;
                }
            }

            double average = sum / grades.size();

            // Display results
            System.out.printf("Average: %.2f\n", average);
            System.out.printf("Highest: %.2f\n", highest);
            System.out.printf("Lowest: %.2f\n", lowest);
        } else {
            System.out.println("No grades were entered.");
        }

        scanner.close();
    }
}
