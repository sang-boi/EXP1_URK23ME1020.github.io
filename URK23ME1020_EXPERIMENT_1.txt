\import java.util.Scanner;

public class ControlStatementsDemo {

    // Helper method to check if a number is prime more efficiently
    public static boolean isPrimeOptimized(int num) {
        if (num <= 1) {
            return false;
        }
        // Check only up to the square root of the number
        for (int j = 2; j <= Math.sqrt(num); j++) {
            if (num % j == 0) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\n===== STUDENT UTILITY APP =====");
            System.out.println("1. Check Even or Odd");
            System.out.println("2. Find Largest of 3 Numbers");
            System.out.println("3. Multiplication Table");
            System.out.println("4. Print Prime Numbers up to N");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");

            // Input validation for non-integer input
            if (!sc.hasNextInt()) {
                System.out.println("Invalid input! Please enter a number between 1 and 5.");
                sc.next(); // Consume the invalid input
                choice = 0; // Force loop to continue with default case
                continue;
            } else {
                choice = sc.nextInt();
            }

            switch (choice) {
                case 1:
                    System.out.print("Enter a number: ");
                    int num = sc.nextInt();
                    if (num % 2 == 0)
                        System.out.println(num + " is EVEN");
                    else
                        System.out.println(num + " is ODD");
                    break;
                case 2:
                    System.out.print("Enter three numbers: ");
                    int a = sc.nextInt();
                    int b = sc.nextInt();
                    int c = sc.nextInt();
                    // A more concise way to find the max
                    int largest = Math.max(a, Math.max(b, c));
                    System.out.println("Largest is: " + largest);
                    break;
                case 3:
                    System.out.print("Enter a number: ");
                    int n = sc.nextInt();
                    for (int i = 1; i <= 10; i++) {
                        System.out.println(n + " x " + i + " = " + (n * i));
                    }
                    break;
                case 4:
                    System.out.print("Enter limit: ");
                    int limit = sc.nextInt();
                    System.out.println("Prime numbers:");
                    for (int i = 2; i <= limit; i++) {
                        if (isPrimeOptimized(i)) {
                            System.out.print(i + " ");
                        }
                    }
                    System.out.println();
                    break;
                case 5:
                    System.out.println("Exiting Application...");
                    break;
                default:
                    System.out.println("Invalid Choice! Try again.");
            }
        } while (choice != 5);
        
        // Ensure the scanner is closed properly to prevent resource leaks
        sc.close();
    }
}
