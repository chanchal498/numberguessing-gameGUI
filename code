
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.Random;

public class NumberGuessingGameGUI extends JFrame {
    // Game Variables
    private int numberToGuess;
    private int attemptsLeft;
    private int score = 0;
    private final int MAX_ATTEMPTS = 7;
    
    // GUI Components
    private JTextField inputField;
    private JLabel feedbackLabel;
    private JLabel attemptsLabel;
    private JLabel scoreLabel;
    private JButton guessButton;
    private JButton playAgainButton;

    public NumberGuessingGameGUI() {
        // 1. Window Setup
        setTitle("✨ Ultimate Guessing Game ✨");
        setSize(500, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(null); // Absolute positioning for total control
        getContentPane().setBackground(new Color(30, 30, 60)); // Black Background

        // 2. Title Label
        JLabel titleLabel = new JLabel("Guess Number (1-100)", SwingConstants.CENTER);
        titleLabel.setFont(new Font("Arial", Font.BOLD, 24));
        titleLabel.setForeground(new Color(255, 215, 0)); // Gold Color
        titleLabel.setBounds(50, 20, 400, 40);
        add(titleLabel);

        // 3. Feedback Label (Main Display)
        feedbackLabel = new JLabel("Enter a number to start!", SwingConstants.CENTER);
        feedbackLabel.setFont(new Font("Verdana", Font.PLAIN, 16));
        feedbackLabel.setForeground(Color.WHITE);
        feedbackLabel.setBounds(50, 70, 400, 30);
        add(feedbackLabel);

        // 4. Input Field
        inputField = new JTextField();
        inputField.setFont(new Font("Arial", Font.BOLD, 18));
        inputField.setHorizontalAlignment(JTextField.CENTER);
        inputField.setBounds(150, 110, 200, 40);
        add(inputField);

        // 5. Guess Button
        guessButton = new JButton("GUESS");
        guessButton.setBackground(new Color(46, 204, 113)); // Emerald Green
        guessButton.setForeground(Color.WHITE);
        guessButton.setFont(new Font("Arial", Font.BOLD, 14));
        guessButton.setBounds(150, 160, 200, 40);
        guessButton.setFocusPainted(false);
        add(guessButton);

        // 6. Attempts & Score
        attemptsLabel = new JLabel("Attempts: " + MAX_ATTEMPTS, SwingConstants.CENTER);
        attemptsLabel.setForeground(new Color(230, 126, 34)); // Orange
        attemptsLabel.setFont(new Font("Arial", Font.BOLD, 14));
        attemptsLabel.setBounds(50, 210, 400, 30);
        add(attemptsLabel);

        scoreLabel = new JLabel("Total Score: 0", SwingConstants.CENTER);
        scoreLabel.setForeground(Color.CYAN);
        scoreLabel.setFont(new Font("Arial", Font.BOLD, 14));
        scoreLabel.setBounds(50, 240, 400, 30);
        add(scoreLabel);

        // 7. Play Again Button (Hidden initially)
        playAgainButton = new JButton("PLAY AGAIN");
        playAgainButton.setBackground(new Color(52, 152, 219)); // Blue
        playAgainButton.setForeground(Color.WHITE);
        playAgainButton.setBounds(150, 280, 200, 40);
        playAgainButton.setVisible(false);
        add(playAgainButton);

        // 8. Add Functionality
        initializeGame();

        // Action: Guess Button Click
        guessButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                checkGuess();
            }
        });

        // Action: Play Again Button Click
        playAgainButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                initializeGame();
            }
        });

        // Center the window on screen
        setLocationRelativeTo(null);
    }

    private void initializeGame() {
        Random rand = new Random();
        numberToGuess = rand.nextInt(100) + 1;
        attemptsLeft = MAX_ATTEMPTS;
        
        feedbackLabel.setText("I picked a number. Start guessing!");
        attemptsLabel.setText("Attempts Left: " + attemptsLeft);
        inputField.setText("");
        inputField.setEditable(true);
        guessButton.setEnabled(true);
        playAgainButton.setVisible(false);
        getContentPane().setBackground(new Color(30, 30, 60)); // Reset BG color
    }

    private void checkGuess() {
        String text = inputField.getText();
        
        // Error Handling
        if (text.isEmpty() || !text.matches("\\d+")) {
            feedbackLabel.setText("❌ Please enter a valid number!");
            return;
        }

        int guess = Integer.parseInt(text);
        attemptsLeft--;

        if (guess == numberToGuess) {
            // WIN CONDITION
            feedbackLabel.setText("🎉 Correct! The number was " + numberToGuess);
            score += (attemptsLeft * 10) + 10;
            scoreLabel.setText("Total Score: " + score);
            endGame(true);
        } else if (attemptsLeft == 0) {
            // LOSE CONDITION
            feedbackLabel.setText("💀 Game Over! It was " + numberToGuess);
            endGame(false);
        } else if (guess < numberToGuess) {
            feedbackLabel.setText("📉 Too Low! Try Higher.");
        } else {
            feedbackLabel.setText("📈 Too High! Try Lower.");
        }

        attemptsLabel.setText("Attempts Left: " + attemptsLeft);
    }

    private void endGame(boolean win) {
        inputField.setEditable(false);
        guessButton.setEnabled(false);
        playAgainButton.setVisible(true);
        
        if (win) {
            getContentPane().setBackground(new Color(39, 174, 96)); // Green background on win
        } else {
            getContentPane().setBackground(new Color(192, 57, 43)); // Red background on loss
        }
    }

    public static void main(String[] args) {
        // Run the GUI safely
        SwingUtilities.invokeLater(() -> {
            new NumberGuessingGameGUI().setVisible(true);
        });
    }
}
