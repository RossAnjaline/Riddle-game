# Riddle-game

This is a simple Riddle Game built in Java, where the user is asked a series of riddles. The player can attempt to answer the riddle, receive hints, and keep track of their score. The game continues until the player decides to stop or all riddles have been answered.

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int score = 0;

        String[] riddles = {
            "I speak without a mouth and hear without ears. I have no body, but I come alive with the wind. What am I?",
            "The more you take, the more you leave behind. What am I?",
            "I'm not alive, but I can grow; I don't have lungs, but I need air; I don't have a mouth, but water kills me. What am I?"
        };

        String[] answers = {
            "An echo",
            "Footsteps",
            "A fire"
        };

        String[] hints = {
            "Hint: This thing is known for its ability to reflect sound.",
            "Hint: Think about what you leave behind when you walk.",
            "Hint: It produces heat and light."
        };

        int numRiddles = riddles.length;

        for (int i = 0; i < numRiddles; i++) {
            String selectedRiddle = riddles[i];
            String correctAnswer = answers[i];
            String hint = hints[i];

            System.out.println("Riddle: " + selectedRiddle);

            String userAnswer = scanner.nextLine();

            if (userAnswer.equalsIgnoreCase(correctAnswer)) {
                System.out.println("Correct!");
                score++;
            } else {
                System.out.println("Wrong! Would you like a hint? (yes/no)");
                String giveHint = scanner.nextLine().toLowerCase();
                if (giveHint.equals("yes")) {
                    System.out.println(hint);
                    System.out.println("Try again! What is your answer?");
                    userAnswer = scanner.nextLine();
                    if (userAnswer.equalsIgnoreCase(correctAnswer)) {
                        System.out.println("Correct!");
                        score++; 
                    } else {
                        System.out.println("Incorrect again. The correct answer was: " + correctAnswer);
                    }
                } else {
                    System.out.println("The correct answer was: " + correctAnswer);
                }
            }

            if (i < numRiddles - 1) {
                System.out.println("Continue playing to the next riddle? (yes/no)");
                String playAgain = scanner.nextLine().toLowerCase();
                if (!playAgain.equals("yes")) {
                    break;
                }
            }
        }

        System.out.println("Your final score: " + score);
        System.out.println("Thanks for playing!");
        scanner.close();
    }
}

