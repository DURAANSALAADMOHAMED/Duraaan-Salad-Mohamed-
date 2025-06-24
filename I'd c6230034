import java.util.Scanner;

public class EVCPlusApp {
    static double balance = 1500.0;
    static int pin = 1234;
    static String[] history = new String[50];
    static int historyIndex = 0;

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Fadlan geli: ");
        String code = input.nextLine();

        if (!code.equals("*770#")) {
            System.out.println("Nambarka aad gelisay waa khalad!");
            return;
        }

        if (!verifyPin(input)) return;

        int option;
        do {
            showMenu();
            option = input.nextInt();
            handleOption(option, input);
        } while (option != 0);

        System.out.println("Mahadsanid isticmaalka EVCPlus App.");
        input.close();
    }

    public static boolean verifyPin(Scanner input) {
        int attempts = 0;
        while (attempts < 3) {
            System.out.print("Fadlan geli PIN-kaaga: ");
            int userPin = input.nextInt();
            if (userPin == pin) {
                return true;
            } else {
                System.out.println("PIN waa khalad. Isku day mar kale.");
                attempts++;
            }
        }
        System.out.println("Waxaad dhaaftay tiradii la oggolaa.");
        return false;
    }

    public static void showMenu() {
        System.out.println("\n--- EVCPlus Menu ---");
        System.out.println("1. Itus Haraaga");
        System.out.println("2. Ku Shub Airtime");
        System.out.println("3. Ugu Shub Airtime");
        System.out.println("4. Bixi Biil");
        System.out.println("5. Uwareeji EVC");
        System.out.println("6. Warbixin Kooban");
        System.out.println("7. Salaam Bank");
        System.out.println("8. Bedel PIN");
        System.out.println("9. Kordhi Xisaabta");
        System.out.println("0. Bixi");
        System.out.print("Dooro adeeg: ");
    }

    public static void handleOption(int option, Scanner input) {
        switch (option) {
            case 1:
                showBalance();
                break;
            case 2:
                kuShubAirtime(input);
                break;
            case 3:
                uguShubAirtime(input);
                break;
            case 4:
                bixiBiil(input);
                break;
            case 5:
                uwareejiEVC(input);
                break;
            case 6:
                showHistory();
                break;
            case 7:
                salaamBankService(input);
                break;
            case 8:
                bedelPIN(input);
                break;
            case 9:
                kordhiXisaab(input);
                break;
            case 0:
                System.out.println("Waad baxday.");
                break;
            default:
                System.out.println("Fadlan dooro number sax ah.");
        }
    }

    public static void showBalance() {
        System.out.printf("Haraagaagu waa: $%.2f\n", balance);
        addToHistory("Haraag la fiiriyay");
    }

    public static void kuShubAirtime(Scanner input) {
        System.out.print("Geli lacagta aad ku shubeyso: ");
        double amount = input.nextDouble();
        if (amount <= 0) {
            System.out.println("Lacag khaldan.");
            return;
        }
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Waad ku shubtay $" + amount);
            addToHistory("Ku shub airtime: $" + amount);
        } else {
            System.out.println("Lacag kuguma filna.");
        }
    }

    public static void uguShubAirtime(Scanner input) {
        System.out.print("Geli numberka: ");
        String number = input.next();
        System.out.print("Geli lacagta: ");
        double amount = input.nextDouble();
        if (amount <= 0) {
            System.out.println("Lacag khaldan.");
            return;
        }
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Waad ugu shubtay $" + amount + " numberka " + number);
            addToHistory("Ugu shub $" + amount + " -> " + number);
        } else {
            System.out.println("Haraaga kuma filna.");
        }
    }

    public static void bixiBiil(Scanner input) {
        System.out.println("1. Biyaha\n2. Koronto\n3. Internet");
        System.out.print("Dooro adeeg: ");
        int biilType = input.nextInt();

        String biilName = "";
        if (biilType == 1) biilName = "Biyaha";
        else if (biilType == 2) biilName = "Koronto";
        else if (biilType == 3) biilName = "Internet";
        else {
            System.out.println("Doorasho khaldan.");
            return;
        }

        System.out.print("Geli lacagta biilka: ");
        double amount = input.nextDouble();
        if (amount <= 0) {
            System.out.println("Lacag khaldan.");
            return;
        }
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Biilka " + biilName + " waa la bixiyay.");
            addToHistory("Biil bixis: " + biilName + " $" + amount);
        } else {
            System.out.println("Haraaga kuma filna.");
        }
    }

    public static void uwareejiEVC(Scanner input) {
        System.out.print("Geli numberka: ");
        String rec = input.next();
        System.out.print("Geli lacagta: ");
        double amount = input.nextDouble();

        if (amount <= 0) {
            System.out.println("Lacag khaldan.");
            return;
        }

        if (amount <= balance) {
            balance -= amount;
            System.out.println("Waad u wareejisay $" + amount + " -> " + rec);
            addToHistory("Wareejin: $" + amount + " -> " + rec);
        } else {
            System.out.println("Haraaga kuma filna.");
        }
    }

    public static void showHistory() {
        System.out.println("--- Warbixin ---");
        for (int i = 0; i < history.length; i++) {
            if (history[i] != null) {
                System.out.println((i + 1) + ". " + history[i]);
            }
        }
    }

    public static void salaamBankService(Scanner input) {
        System.out.println("1. Ku xir Salaam Bank\n2. Ka jooji");
        int choice = input.nextInt();
        if (choice == 1) {
            System.out.print("Geli account number: ");
            String acc = input.next();
            System.out.println("Waad ku xiratay account-ka " + acc);
            addToHistory("Xiriir Salaam Bank: " + acc);
        } else if (choice == 2) {
            System.out.println("Xiriirka Salaam Bank waa la joojiyay.");
            addToHistory("Joojis Salaam Bank.");
        } else {
            System.out.println("Doorasho khaldan.");
        }
    }

    public static void bedelPIN(Scanner input) {
        System.out.print("Geli PIN-kii hore: ");
        int oldPin = input.nextInt();
        if (oldPin == pin) {
            System.out.print("Geli PIN cusub: ");
            int newPin = input.nextInt();
            System.out.print("Ku celi PIN cusub: ");
            int confirmPin = input.nextInt();
            if (newPin == confirmPin) {
                pin = newPin;
                System.out.println("PIN waa la bedelay.");
                addToHistory("PIN waa la bedelay.");
            } else {
                System.out.println("PIN-ku isma lahan.");
            }
        } else {
            System.out.println("PIN hore waa khalad.");
        }
    }

    public static void kordhiXisaab(Scanner input) {
        System.out.print("Geli lacagta aad rabto inaad ku kordhiso: ");
        double amount = input.nextDouble();
        if (amount <= 0) {
            System.out.println("Lacag khaldan.");
            return;
        }
        balance += amount;
        System.out.println("Haraaga cusub: $" + balance);
        addToHistory("Kordhis: $" + amount);
    }

    public static void addToHistory(String action) {
        if (historyIndex < history.length) {
            history[historyIndex] = action;
            historyIndex++;
        } else {
            // Circular overwrite
            historyIndex = 0;
            history[historyIndex] = action;
            historyIndex++;
        }
    }
}
