import java.util.ArrayList;
import java.util.Scanner;

class Product {
    String name;
    double price;

    Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String show() {
        return name + " - ₱" + price;
    }
}

public class InventorySystem {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        ArrayList<Product> products = new ArrayList<>();

        while (true) {
            System.out.println("\n Inventory Products ");
            System.out.println("1. Add Product");
            System.out.println("2. View Products");
            System.out.println("3. Update Product");
            System.out.println("4. Delete Product");
            System.out.print("Choose: ");

            int choice = input.nextInt();
            input.nextLine();

            if (choice == 1) {
                System.out.print("Product name: ");
                String name = input.nextLine();
                System.out.print("Price: ");
                double price = input.nextDouble();
                input.nextLine();

                products.add(new Product(name, price));
                System.out.println("Product added.");

            } else if (choice == 2) {
                if (products.isEmpty()) {
                    System.out.println("No products found.");
                } else {
                    for (int i = 0; i < products.size(); i++) {
                        System.out.println((i + 1) + ". " + products.get(i).show());
                    }
                }

            } else if (choice == 3) {
                System.out.print("Product number: ");
                int index = input.nextInt() - 1;
                input.nextLine();

                if (index >= 0 && index < products.size()) {
                    System.out.print("New name: ");
                    products.get(index).name = input.nextLine();
                    System.out.print("New price: ");
                    products.get(index).price = input.nextDouble();
                    input.nextLine();
                    System.out.println("Product updated.");
                }

            } else if (choice == 4) {
                System.out.print("Product number: ");
                int index = input.nextInt() - 1;

                if (index >= 0 && index < products.size()) {
                    products.remove(index);
                    System.out.println("Product deleted.");
                }

            } else {
                System.out.println("Invalid choice.");
            }
        }
    }
}
