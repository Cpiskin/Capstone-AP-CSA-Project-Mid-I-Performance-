class BankAccount {

    private String name;
    private String pin;
    private int number;
    private double balance;

    // Singleton instance
    private static BankAccount instance;

    // Constructor
    private BankAccount(String name, String pin, int number, double balance) {
        this.name = name;
        this.pin = pin;
        this.number = number;
        this.balance = balance;
    }

    // Singleton getInstance method
    public static BankAccount getInstance(String name, String pin, int number, double balance) {
        if (instance == null) {
            instance = new BankAccount(name, pin, number, balance);
        }
        return instance;
    }

    // Setters
    public void setName(String name) {
        this.name = name;
    }

    public void setPin(String pin) {
        this.pin = pin;
    }

    public void setNumber(int number) {
        this.number = number;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    // Getters
    public String getName() {
        return name;
    }

    public String getPin() {
        return pin;
    }

    public int getNumber() {
        return number;
    }

    public double getBalance() {
        return balance;
    }
}



