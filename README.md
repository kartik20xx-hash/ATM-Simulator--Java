# ATM Simulator (Java)

## Description
A console-based ATM system with:
- PIN authentication (3 attempts)
- Deposit and withdrawal
- Balance checking

## Concepts Used
- Loops
- Conditional statements
- Functions

## How to Run
javac Main.java
java Main

##code 

import java.util.*;
public class Main{
    public static int deposit(int balance,int amount){
        balance = balance+amount;
        System.out.println("CURRENT BALANCE "+balance);
        return  balance;
    }

    public static int  withdraw(int balance,int amount) {
        if (balance >= amount) {
            balance = balance - amount;
            System.out.println("CURRENT BALANCE " +balance);}
        else {System.out.println("insufficient amount");}

        return balance;
    }


    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int i = 0;
        while (i <3) {
            System.out.println("ENTER PIN CODE");
            int pin = sc.nextInt();
            if (pin == 1234) {
                System.out.println("CORRECT PIN");
                System.out.println("ENTER  INTIAL BALANCE");
                int balance = sc.nextInt();
                while (true) {
                    System.out.println("ENTER BUTTON:");
                    System.out.println("1 FOR DEPOSIT");
                    System.out.println("2 FOR WITHDRAW");
                    System.out.println("3 FOR CHECK BALANCE");
                    System.out.println("4 FOR EXIT");
                    int button = sc.nextInt();
                    switch (button) {
                        case 1:
                            System.out.println("ENTER AMOUNT");
                            int amount = sc.nextInt();
                            balance = deposit(balance, amount);
                            break;
                        case 2:
                            System.out.println("ENTER AMOUNT");
                            amount = sc.nextInt();
                            balance = withdraw(balance, amount);
                            break;
                        case 3:
                            System.out.println("CURRENT BALANCE" + balance);
                            break;
                        case 4:
                            System.out.println("THANK YOU");
                            return;
                        default:
                            System.out.println("INVALID BUTTON");
                            break;
                    }
                }
            }
            else{i++;
                System.out.println(3-i+"ATTEMPT REMAINING");}
            if(i==3){
                System.out.println("CARD BLOCK");
                return;
            }
        }
    }
}
