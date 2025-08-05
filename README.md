# Java-Queue
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package com.mycompany.bankqueue;
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;
/**
 *
 * @author carlc
 */
class Customer {
    private static int counter = 1;
    private final String name;
    private final int number;

    public Customer(String name) {
        this.name = name;
        this.number = counter++;
    }

    public String getName() {
        return name;
    }

    public int getNumber() {
        return number;
    }

    public String toString() {
        return "Customer No: " + number + ", Name: " + name;
    }
}

public class Bankqueue {

    public static void main(String[] args) {
         Scanner scanner = new Scanner(System.in);
        Queue<Customer> queue = new LinkedList<>();
        boolean running = true;

        while (running) {
            System.out.println("\n--- Bank Queue Menu ---");
            System.out.println("1. Add customer to queue");
            System.out.println("2. Serve next customer");
            System.out.println("3. View queue");
            System.out.println("4. Exit");
            System.out.print("Select an option (1-4): ");

            String choice = scanner.nextLine();
switch (choice) {
                case "1":
                    System.out.print("Enter customer name: ");
                    String name = scanner.nextLine();
                    Customer newCustomer = new Customer(name);
                    queue.add(newCustomer);
                    System.out.println(newCustomer + " added to the queue.");
                    break;

                case "2":
                    if (queue.isEmpty()) {
                        System.out.println("Queue is empty. No customer to serve.");
                    } else {
                        Customer served = queue.poll();
                        System.out.println("Serving customer -> " + served);
                    }
                    break;
                    case "3":
                    if (queue.isEmpty()) {
                        System.out.println("Queue is empty.");
                    } else {
                        System.out.println("Current queue:");
                        for (Customer customer : queue) {
                            System.out.println(customer);
                        }
                    }
                    break;

                case "4":
                    running = false;
                    System.out.println("Exiting program. Goodbye!");
                    break;

                default:
                    System.out.println("Invalid option. Please try again.");
            }
                }

        scanner.close();
    }
}

    

