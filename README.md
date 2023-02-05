# Basic-Payment-app-Java-
 HI, this is a basic java application for payments where user is asked to login and select the options like Add money, Send moneny and even can see the transcation history.

Application description:
 this java program is regarding the transactions done by the users. The program takes the inputs from the users, for staters the program asks the users for the login credentials and verify them. If right, then it shows the options which are "send money", "add money", "transactions history" and "quit". when "add money" option is selected by the user they can add the money to their account and it shows the updated balance. If the user selects "send money" option the program asks the users to give the user details and verify them and asks the amount the user want to send. "Transaction history" the 3 option which shows what type of transactions were done by the user. "Quit" is the final option through which the user can logout of the payment app and a message pop's up saying thank you for using me. I've taken all the test cases as successfull. 


 Here is the code:


import java.util.Scanner;

public class Main {
    private static String userId;
    private static int userPin;
    private static double balance;
    private static String[] transactions;
    private static int transactionCount;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welcome to Payment App");
        System.out.println("Enter your user id: ");
        userId = scanner.nextLine();
        System.out.println("Enter your user pin: ");
        userPin = scanner.nextInt();
        transactions = new String[10];
        transactionCount = 0;

        if (isValidCredentials(userId, userPin)) {
            System.out.println("Login successful!");
            while (true) {
                System.out.println("1. Send Money");
                System.out.println("2. Add Money");
                System.out.println("3. Transactions History");
                System.out.println("4. Quit");
                System.out.println("Enter your choice: ");

                int choice = scanner.nextInt();
                scanner.nextLine();

                switch (choice) {
                    case 1:
                         sendMoney();
                        break;
                    case 2:
                        addMoney();
                        break;
                    case 3:
                        printTransactionHistory();
                        break;
                    case 4:
                        quit();
                        break;
                }
            }
        } else {
            System.out.println("Invalid user id or pin. Please try again.");
        }
    }

    private static boolean isValidCredentials(String userId, int userPin) {
        String[][] validUsers = {{"user1", "1234"}, {"user2", "2345"}, {"user3", "3456"}};

    for (String[] validUser : validUsers) {
        if (validUser[0].equals(userId) && Integer.parseInt(validUser[1]) == userPin) {
            return true;
        }
    }
    return false;
    }
    private static void sendMoney() {
         Scanner scanner = new Scanner(System.in);
   
    System.out.println("Enter user id: ");
    String recipientId = scanner.nextLine();
    System.out.println("Enter user pin: ");
    int recipientPin = scanner.nextInt();
   
    if (isValidCredentials(recipientId, recipientPin)) {
        System.out.println("user login successful!");
        System.out.println("Enter the amount to send: ");
        double amount = scanner.nextDouble();
        System.out.println("Transaction is successfull");
       }
       else {
        System.out.println("Invalid recipient user id or pin. Please try again.");
       }
    transactions[transactionCount] = "Money sent";
    transactionCount++;
    }
    private static void addMoney() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the amount you want to add: ");
        double amount = scanner.nextDouble();
        balance += amount;
        System.out.println("Amount added successfully. Your new balance is: " + balance);
    
    transactions[transactionCount] = "Money added";
    transactionCount++;
    }

    private static void printTransactionHistory() {
        System.out.println("Transaction history:");
    for (int i = 0; i < transactionCount; i++) {
        System.out.println(transactions[i]);
    }
    }

    private static void quit() {
        System.out.println("Thank you for using me");
        System.exit(0);
    }
}
