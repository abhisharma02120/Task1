# Task1
import java.util.Scanner;
import java.util.Random;

public class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int maxAttempts = 5;  // Maximum number of attempts allowed
        boolean playAgain = true;
        int roundsWon = 0;

        while (playAgain) {
            int numberToGuess = random.nextInt(100) + 1; // Random number between 1 and 100
            int attempts = 0;
            boolean hasWon = false;

            System.out.println("Guess a number between 1 and 100. You have " + maxAttempts + " attempts.");

            while (attempts < maxAttempts) {
                attempts++;
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();

                if (userGuess == numberToGuess) {
                    System.out.println("Congratulations! You've guessed the number correctly in " + attempts + " attempts.");
                    hasWon = true;
                    roundsWon++;
                    break;
                } else if (userGuess < numberToGuess) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }
            }

            if (!hasWon) {
                System.out.println("Sorry, you've used all your attempts. The number was " + numberToGuess + ".");
            }

            System.out.println("You've won " + roundsWon + " rounds so far.");
            System.out.print("Do you want to play again? (yes/no): ");
            String userResponse = scanner.next();

            playAgain = userResponse.equalsIgnoreCase("yes");
        }

        System.out.println("Thank you for playing! Your total rounds won: " + roundsWon);
        scanner.close();
    }
}
