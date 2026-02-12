# project-3
import java.util.*;

public class SupermarketBillingQueue {

    static Queue<String> customerQueue = new LinkedList<>();
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {

        int choice;

        do {
            System.out.println("\n===== SUPERMARKET BILLING =====");
            System.out.println("1. Add Customer");
            System.out.println("2. Process Billing");
            System.out.println("3. Show Pending Customers");
            System.out.println("4. Exit");
            System.out.print("Enter choice: ");

            choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {

                case 1:
                    addCustomer();
                    break;

                case 2:
                    processBilling();
                    break;

                case 3:
                    showCustomers();
                    break;

                case 4:
                    System.out.println("Exiting...");
                    break;

                default:
                    System.out.println("Invalid choice!");
            }

        } while (choice != 4);
    }

    // Add Customer
    static void addCustomer() {

        System.out.print("Enter customer name: ");
        String name = sc.nextLine();

        customerQueue.add(name);
        System.out.println("Customer added to queue!");
    }

    // Process Billing
    static void processBilling() {

        if (customerQueue.isEmpty()) {
            System.out.println("No customers in queue!");
            return;
        }

        String name = customerQueue.remove();
        System.out.println("\nBilling for: " + name);

        System.out.print("Enter number of items: ");
        int n = sc.nextInt();
        sc.nextLine();

        String[] items = new String[n];  
        Stack<String> stack = new Stack<>(); 

        for (int i = 0; i < n; i++) {
            System.out.print("Enter item " + (i + 1) + ": ");
            items[i] = sc.nextLine();
            stack.push(items[i]);
        }

        System.out.println("Items (Reverse Order):");
        while (!stack.isEmpty()) {
            System.out.println(stack.pop());
        }

        System.out.println("Billing completed for " + name);
    }

    // Show Pending Customers
    static void showCustomers() {

        if (customerQueue.isEmpty()) {
            System.out.println("No pending customers.");
            return;
        }

        System.out.println("\nPending Customers:");
        for (String name : customerQueue) {
            System.out.println(name);
        }
    }
}

<img width="695" height="710" alt="Screenshot 2026-02-12 133440" src="https://github.com/user-attachments/assets/774b91ba-c027-4ee1-823a-53170b04c8d5" />
