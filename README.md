# JTask1
import java.util.Random;
import java.util.Scanner;

public class NumberGame {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        boolean playAgain = true;
        int totalAttempts = 0;
        int totalGames = 0;
        
        while (playAgain) {
            int secretNumber = random.nextInt(100) + 1;
            int attempts = 0;
            boolean guessedCorrectly = false;
            
            System.out.println("Welcome to the Number Guessing Game!");
            System.out.println("I've picked a number between 1 and 100. Try to guess it!");

            while (!guessedCorrectly && attempts < 5) { // Limiting attempts to 5
                System.out.print("Enter your guess (1-100): ");
                int guess = scanner.nextInt();
                scanner.nextLine(); // Consume newline character
                
                attempts++;
                
                if (guess < secretNumber) {
                    System.out.println("Too low! Try again.");
                } else if (guess > secretNumber) {
                    System.out.println("Too high! Try again.");
                } else {
                    guessedCorrectly = true;
                    System.out.println("Congratulations! You've guessed the number (" + secretNumber + ") in " + attempts + " attempts.");
                }
            }
            
            if (!guessedCorrectly) {
                System.out.println("Sorry, you've run out of attempts. The number was: " + secretNumber);
            }
            
            totalAttempts += attempts;
            totalGames++;
            
            System.out.print("Do you want to play again? (yes/no): ");
            String playChoice = scanner.nextLine();
            
            if (!playChoice.equalsIgnoreCase("yes")) {
                playAgain = false;
                System.out.println("Thanks for playing! Here are your stats:");
                System.out.println("Total games played: " + totalGames);
                System.out.println("Total attempts: " + totalAttempts);
            }
        }
        
        scanner.close();
    }
}
