import java.util.*;
class BankAccount{
    private double balance;
    public BankAccount(double initialBalance){
        balance=initialBalance;
    }
    public void deposit(double amount){
        if (amount>0){
            balance+=amount;
            System.out.println("Successfully deposited: Rs." + amount);
        }
        else{
            System.out.println("Deposit amount must be positive.");
        }
    }
    public void withdraw(double amount){
        if (amount>0){
            if (amount<=balance){
                balance-=amount;
                System.out.println("Successfully withdrawn: Rs." + amount);
            }
            else{
                System.out.println("Insufficient balance.");
            }
        }else
        {
            System.out.println("Withdrawal amount must be positive.");
        }
    }
    public double getBalance(){
        return balance;
    }
}
public class BankingSystem{
    public static void main(String[] args){
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter initial balance: ");
        double initialBalance=scanner.nextDouble();
        BankAccount account=new BankAccount(initialBalance);
        int choice;
        do{
            System.out.println("\n--- Banking System Menu ---");
            System.out.println("1. Deposit");
            System.out.println("2. Withdraw");
            System.out.println("3. Check Balance");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            choice=scanner.nextInt();
            switch(choice){
                case 1:
                    System.out.print("Enter amount to deposit: ");
                    double depositAmount = scanner.nextDouble();
                    account.deposit(depositAmount);
                    break;
                case 2:
                    System.out.print("Enter amount to withdraw: ");
                    double withdrawAmount = scanner.nextDouble();
                    account.withdraw(withdrawAmount);
                    break;
                case 3:
                    System.out.println("Your current balance is: Rs."+account.getBalance());
                    break;
                case 4:
                    System.out.println("Thank you for using the banking system.");
                    break;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }while(choice!=4);
        scanner.close();
    }
}
