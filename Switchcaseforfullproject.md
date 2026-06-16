import java.util.Scanner;

public class Main {

    public static void main(String[] args) throws Exception {

        Scanner sc = new Scanner(System.in);
        BookDAO dao = new BookDAO();

        while(true) {

            System.out.println("\n===== LIBRARY MANAGEMENT SYSTEM =====");
            System.out.println("1 Insert Book");
            System.out.println("2 Update Price");
            System.out.println("3 Delete Book");
            System.out.println("4 Display By Category");
            System.out.println("5 Exit");

            System.out.print("Enter Choice: ");
            int ch = sc.nextInt();

            switch(ch) {

                case 1:

                    System.out.print("Enter Book ID: ");
                    int id = sc.nextInt();
                    sc.nextLine();

                    System.out.print("Enter Title: ");
                    String title = sc.nextLine();

                    System.out.print("Enter Author: ");
                    String author = sc.nextLine();

                    System.out.print("Enter Category: ");
                    String category = sc.nextLine();

                    System.out.print("Enter Price: ");
                    double price = sc.nextDouble();

                    Book b = new Book(
                            id,
                            title,
                            author,
                            category,
                            price
                    );

                    dao.insertBook(b);

                    System.out.println("Book Inserted Successfully");
                    break;

                case 2:

                    System.out.print("Enter Book ID: ");
                    int bookId = sc.nextInt();

                    System.out.print("Enter New Price: ");
                    double newPrice = sc.nextDouble();

                    dao.updatePrice(bookId, newPrice);

                    System.out.println("Price Updated Successfully");
                    break;

                case 3:

                    System.out.print("Enter Book ID to Delete: ");
                    int deleteId = sc.nextInt();

                    dao.deleteBook(deleteId);

                    System.out.println("Book Deleted Successfully");
                    break;

                case 4:

                    sc.nextLine();

                    System.out.print("Enter Category: ");
                    String cat = sc.nextLine();

                    System.out.println("\nBooks in Category: " + cat);
                    dao.displayCategory(cat);

                    break;

                case 5:

                    System.out.println("Thank You");
                    System.exit(0);

                default:

                    System.out.println("Invalid Choice");
            }
        }
    }
}







book.java


public class Book {

    private int bookId;
    private String title;
    private String author;
    private String category;
    private double price;

    public Book() {}

    public Book(int bookId, String title, String author,
                String category, double price) {

        this.bookId = bookId;
        this.title = title;
        this.author = author;
        this.category = category;
        this.price = price;
    }

    public int getBookId() {
        return bookId;
    }

    public String getTitle() {
        return title;
    }

    public String getAuthor() {
        return author;
    }

    public String getCategory() {
        return category;
    }

    public double getPrice() {
        return price;
    }
}
