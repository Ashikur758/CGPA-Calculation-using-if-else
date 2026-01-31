import java.util.Scanner;

public class CgpaCalculation{
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input student ID
        System.out.print("Student ID: ");
        String studentID = sc.nextLine();

        // Input number of courses
        System.out.print("No. of Courses: ");
        int n = sc.nextInt();

        int totalCreditTaken = 0;
        int totalCreditEarned = 0;
        double totalGradePoints = 0;

        for (int i = 1; i <= n; i++) {
            System.out.println("C" + i + ":");
            System.out.print("  Credit (Max 3): ");
            int credit = sc.nextInt();

            System.out.print("  CT (Max 30): ");
            int ct = sc.nextInt();

            System.out.print("  AT (Max 10): ");
            int at = sc.nextInt();

            System.out.print("  FE (Max 60): ");
            int fe = sc.nextInt();

            int totalMarks = ct + at + fe;
            double gradePoint = 0;

            // Determine grade point using total marks
            if (totalMarks >= 80) {
                gradePoint = 4.0;
            } else if (totalMarks >= 75) {
                gradePoint = 3.75;
            } else if (totalMarks >= 70) {
                gradePoint = 3.5;
            } else if (totalMarks >= 65) {
                gradePoint = 3.25;
            } else if (totalMarks >= 60) {
                gradePoint = 3.0;
            } else if (totalMarks >= 55) {
                gradePoint = 2.75;
            } else if (totalMarks >= 50) {
                gradePoint = 2.5;
            } else if (totalMarks >= 45) {
                gradePoint = 2.25;
            } else if (totalMarks >= 40) {
                gradePoint = 2.0;
            } else {
                gradePoint = 0;
            }

            totalCreditTaken += credit;
            if (gradePoint > 0) {
                totalCreditEarned += credit;
            }

            totalGradePoints += gradePoint * credit;
        }

        // Calculate CGPA
        double cgpa = totalGradePoints / totalCreditTaken;

        // Determine final grade
        String finalGrade;
        if (cgpa >= 4.0) {
            finalGrade = "A+";
        } else if (cgpa >= 3.75) {
            finalGrade = "A";
        } else if (cgpa >= 3.5) {
            finalGrade = "A-";
        } else if (cgpa >= 3.25) {
            finalGrade = "B+";
        } else if (cgpa >= 3.0) {
            finalGrade = "B";
        } else if (cgpa >= 2.75) {
            finalGrade = "B-";
        } else if (cgpa >= 2.5) {
            finalGrade = "C+";
        } else if (cgpa >= 2.25) {
            finalGrade = "C";
        } else if (cgpa >= 2.0) {
            finalGrade = "D";
        } else {
            finalGrade = "F";
        }

        // Output results
        System.out.println("\nStudent ID: " + studentID);
        System.out.println("Credit Taken: " + totalCreditTaken);
        System.out.println("Credit Earned: " + totalCreditEarned);
        System.out.printf("CGPA: %.2f\n", cgpa);
        System.out.println("Grade: " + finalGrade);

        sc.close();
    }
}
