# AMAZONSHOPPINGROJECT
1. AMAZON SHOPPING PROJECT • Developed a Project for Online Shopping Platform: Designed and implemented a Java-based online shopping platform, simulating the shopping experience on Amazon. • Utilized Technologies and Tools: Employed Java programming language for backend development, and used HashMap for data storage. 
#Product
public class Product {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getPassword() {
        return password;
    }

    public void setPassword(int password) {
        this.password = password;
    }

    private int password;

    public Product(String name, int password) {
        this.name = name;
        this.password = password;
    }

    @Override
    public String toString() {
        return "Product{" +
                "name='" + name + '\'' +
                ", password=" + password +
                '}';
    }
}
#Customer
package Amazon;

public class Customer {
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getPassword() {
        return password;
    }

    public void setPassword(int password) {
        this.password = password;
    }

    public Customer(String name, int password) {
        this.name = name;
        this.password = password;
    }

    private String name;
    private int password;

    @Override
    public String toString() {
        return "Customer{" +
                "name='" + name + '\'' +
                ", password=" + password +
                '}';
    }
}
#BLClass
package Amazon;

import java.util.HashMap;

public class BLClass {

    private HashMap<String, Double> productMap = new HashMap<>();

    public void buyProduct(String productName, double productPrice) {
        productMap.put(productName, productPrice);
        System.out.println("Product bought: " + productName);
    }

    public void cancelProduct(String productName) {
        if (productMap.containsKey(productName)) {
            productMap.remove(productName);
            System.out.println("Product canceled: " + productName);
        } else {
            System.out.println("Product not found");
        }
    }

    public void displayAllProducts() {
        for (String productName : productMap.keySet()) {
            System.out.println(productName + ": " + productMap.get(productName));
        }
    }
}
#MainApp
package Amazon;
import java.util.HashMap;
import java.util.Scanner;
public class MainApp1 {
    static HashMap<String, String> userMap = new HashMap<>();
    static Scanner sc = new Scanner(System.in);
    static BLClass bl = new BLClass();


    public static void main(String[] args) {
        // Add some users to the userMap
        userMap.put("user1", "password1");
        userMap.put("user2", "password2");


        boolean status = false;
        while (!status) {
            displayMenu();
            int choice = sc.nextInt();
            switch (choice) {
                case 1:
                    login();
                    break;
                case 2:
                    buyProduct();
                    break;
                case 3:
                    cancelProduct();
                    break;
                case 4:
                    bl.displayAllProducts();
                    break;
                case 5:
                    logout();
                    break;
                case 6:
                    status = true;
                    break;
                default:
                    System.out.println("Invalid choice");
            }
        }
    }

    private static void displayMenu() {
        System.out.println("=================================");
        System.out.println("1. Log in");
        System.out.println("2. Buy product");
        System.out.println("3. Cancel product");
        System.out.println("4. Display all products");
        System.out.println("5. Sign out");
        System.out.println("6. Exit");
        System.out.println("==================================");
        System.out.print("Enter your choice: ");
    }

    private static void login() {
        System.out.print("Enter username: ");
        String username = sc.next();
        System.out.print("Enter password: ");
        int password = sc.nextInt();
        if (userMap.containsKey(username)) {
            userMap.get(username);
        }


        System.out.println("Login successful");
        }  {
            System.out.println("Invalid username or password");
        }


        private static void buyProduct() {
            int loggedInUser=0;
            if (loggedInUser == 0) {
                System.out.print("Enter product name: ");
                String productName = sc.next();
                System.out.print("Enter product price: ");
                double productPrice = sc.nextDouble();
                bl.buyProduct(productName, productPrice);
            } else {
                System.out.println("You need to log in first");
            }
        }

        private static void cancelProduct() {
            int loggedInUser=0;
            if (loggedInUser == 0) {
                System.out.print("Enter product name: ");
                String productName = sc.next();
                bl.cancelProduct(productName);
            } else {
                System.out.println("You need to log in first");
            }
        }

        private static void logout() {
            System.out.println("Logged out");
        }
    }
