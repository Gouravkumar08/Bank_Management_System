import java.util.Scanner;
import java.util.HashMap;
import java.util.Map;

public class Bank_Management_System {
    private UserManager userManager = new UserManager();

    public class User {
        private String username;
        private String password;
        private double balance;

        public User(String username, String password, double balance) {
            this.username = username;
            this.password = password;
            this.balance = balance;
        }

        // Getters and setters
        public String getUsername() {
            return username;
        }

        public void setUsername(String username) {
            this.username = username;
        }

        // Password getter (for security reasons, no setter for password in this example)
        public String getPassword() {
            return password;
        }

        public double getBalance() {
            return balance;
        }

        public void setBalance(double balance) {
            this.balance = balance;
        }
    }

    public class UserManager {
        private Map<String, User> users;

        public UserManager() {
            this.users = new HashMap<>();
        }

        public void addUser(String username, String password, double balance) {
            if (!users.containsKey(username)) {
                User newUser = new User(username, password, balance);
                users.put(username, newUser);
                System.out.println("User created successfully.");
            } else {
                System.out.println("Username already exists. Please choose another username.");
            }
        }

        public boolean loginUser(String username, String password) {
            if (users.containsKey(username)) {
                User user = users.get(username);
                if (user.getPassword().equals(password)) {
                    System.out.println("Login successful.");
                    return true;
                } else {
                    System.out.println("Invalid password. Please try again.");
                }
            } else {
                System.out.println("User not found. Please signup.");
            }
            return false;
        }

        public User getUser(String username) {
            return users.get(username);
        }
    }

    public static void main(String[] args) {
        Bank_Management_System bankManagementSystem = new Bank_Management_System();
        Scanner scanner = new Scanner(System.in);

        boolean exit = false;
        while (!exit) {
            System.out.println("Welcome to the Bank Management System.");
            System.out.println("1. Signup");
            System.out.println("2. Login");
            System.out.println("3. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline after reading integer

            switch (choice) {
                case 1:
                    System.out.print("Enter username: ");
                    String signupUsername = scanner.nextLine();
                    System.out.print("Enter password: ");
                    String signupPassword = scanner.nextLine();
                    System.out.print("Enter initial balance: ");
                    double initialBalance = scanner.nextDouble();
                    scanner.nextLine(); // Consume newline after reading double
                    bankManagementSystem.userManager.addUser(signupUsername, signupPassword, initialBalance);
                    break;
                case 2:
                    System.out.print("Enter username: ");
                    String loginUsername = scanner.nextLine();
                    System.out.print("Enter password: ");
                    String loginPassword = scanner.nextLine();
                    if (bankManagementSystem.userManager.loginUser(loginUsername, loginPassword)) {
                        // Logged in successfully
                        Bank_Management_System.User loggedInUser = bankManagementSystem.userManager.getUser(loginUsername);
                        System.out.println("Welcome, " + loggedInUser.getUsername() + "!");
                        System.out.println("Your balance is: $" + loggedInUser.getBalance());
                        // Add banking operations here
                    }
                    break;
                case 3:
                    exit = true;
                    System.out.println("Exiting Bank Management System. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid option. Please choose again.");
            }
        }

        scanner.close();
    }
}
