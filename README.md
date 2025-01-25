# Daily-expenses-In-java-
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class DailyExpenses {
    
    private static Map<String, Double> expenses = new HashMap<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String date;
        double amount;
        
        while (true) {
            System.out.println("Enter the date (YYYY-MM-DD) or type 'exit' to quit:");
            date = scanner.nextLine();
            
            if (date.equalsIgnoreCase("exit")) {
                break;
            }
            
            System.out.println("Enter the expense amount for " + date + ":");
            amount = scanner.nextDouble();
            scanner.nextLine();
            
        
            addExpense(date, amount);
        }
        
        displayExpenses();
        
        scanner.close();
    }

    private static void addExpense(String date, double amount) {
      
        if (expenses.containsKey(date)) {
            double existingAmount = expenses.get(date);
            expenses.put(date, existingAmount + amount);
        } else {
            expenses.put(date, amount);
        }
    }

    private static void displayExpenses() {
       
        System.out.println("Daily Expenses:");
        for (Map.Entry<String, Double> entry : expenses.entrySet()) {
            System.out.println("Date: " + entry.getKey() + ", Amount: " + entry.getValue());
        }
    }
}
