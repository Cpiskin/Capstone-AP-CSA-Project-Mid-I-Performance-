import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class BankAccountPanel extends JFrame {

    private JTextField nameField, pinField, numberField, balanceField;
    private JButton displayButton;

    private BankAccount bankAccount; // Added BankAccount instance

    public BankAccountPanel() {
        // Setting up the JFrame
        super("Bank Account Information");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(300, 200);
        setLocationRelativeTo(null);

        // Creating BankAccount instance using getInstance method
        bankAccount = BankAccount.getInstance("", "", 0, 0.0);

        // Creating components
        nameField = new JTextField(20);
        pinField = new JTextField(20);
        numberField = new JTextField(20);
        balanceField = new JTextField(20);
        displayButton = new JButton("Display Information");

        // Setting up layout
        setLayout(new GridLayout(5, 2));
        add(new JLabel("Name:"));
        add(nameField);
        add(new JLabel("PIN:"));
        add(pinField);
        add(new JLabel("Number:"));
        add(numberField);
        add(new JLabel("Balance:"));
        add(balanceField);
        add(new JLabel(""));
        add(displayButton);

        // Adding action listener to the button
        displayButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                // Display information when the button is clicked
                displayInformation();
            }
        });
    }

    private void displayInformation() {
        // Retrieving information from text fields
        String name = nameField.getText();
        String pin = pinField.getText();
        int number = Integer.parseInt(numberField.getText());
        double balance = Double.parseDouble(balanceField.getText());

        // Setting information to the BankAccount instance
        bankAccount.setName(name);
        bankAccount.setPin(pin);
        bankAccount.setNumber(number);
        bankAccount.setBalance(balance);

        // Displaying the information in console
        System.out.println("Name: " + bankAccount.getName());
        System.out.println("PIN: " + bankAccount.getPin());
        System.out.println("Number: #" + bankAccount.getNumber());
        System.out.println("Balance: $" + bankAccount.getBalance());

        // Displaying the information on the JPanel
        updatePanelWithInformation();
    }

    private void updatePanelWithInformation() {
        // Setting the information in text fields
        nameField.setText(bankAccount.getName());
        pinField.setText(bankAccount.getPin());
        numberField.setText(Integer.toString(bankAccount.getNumber()));
        balanceField.setText(Double.toString(bankAccount.getBalance()));
    }

    public static void main(String[] args) {
        // Create and show the GUI
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new BankAccountPanel().setVisible(true);
            }
        });
    }
}
