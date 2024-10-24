# HelloWorld
Hello World!

This is my first commit


This is my second commit!




package org.lbg.c4;

import java.util.Scanner;

/**
 * Hello world!
 */
public class App {
    public static void main(String[] args) {

        Scanner calc = new Scanner(System.in);
        System.out.print("Enter the VAT rate: ");
        double vatRate = Double.parseDouble(calc.nextLine());

        double totalCost = 0.0;
        String exitCode = "";

        while (true) {
            System.out.print("Enter the cost of an item (or type 'QUIT' to finish): ");
            exitCode = calc.nextLine();

            if (exitCode.equalsIgnoreCase("QUIT")) {
                break;
            }

            try {
                double itemCost = Double.parseDouble(exitCode);
                totalCost += itemCost; // Add the item cost to the total cost
            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter a valid number or 'QUIT' to finish.");
            }
        }

        System.out.println("The total cost is: £ " + String.format("%.2f", addVat(totalCost, vatRate)));
        calc.close();
    }

    public static double addVat(double cost, double vatRate) {
        return cost + (cost * (vatRate / 100));
    }
}
