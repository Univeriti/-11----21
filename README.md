mport java.util.Scanner;
import java.io.FileWriter;
import java.io.FileReader;
import java.io.BufferedReader;
import java.io.IOException;

public class {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Меню:");
            System.out.println("1. Записати до файлу");
            System.out.println("2. Прочитати вміст файлу");
            System.out.println("3. Вийти з редактора");

            String choice = scanner.nextLine();

            if (choice.equals("1")) {
                writeToFile(scanner);
            } else if (choice.equals("2")) {
                readFromFile();
            } else if (choice.equals("3")) {
                System.out.println("Вихід з редактора");
                break;
            } else {
                System.out.println("Невірний вибір");
            }
        }
    }

    public static void writeToFile(Scanner scanner) {
        try {
            FileWriter writer = new FileWriter("data.txt", false);
            System.out.println("Введіть рядки для запису. Щоб завершити ");
            while (true) {
                String line = scanner.nextLine();
                if (line.isEmpty()) break;
                writer.write(line + "\n");
            }
            writer.close();
            System.out.println("Дані записано у файл.");
        } catch (IOException e) {
            System.out.println("Помилка запису у файл.");
        }
    }
public static void readFromFile() {
        try {
            FileReader fileReader = new FileReader("data.txt");
            BufferedReader reader = new BufferedReader(fileReader);

            String line;
            System.out.println("Вміст файлу:");
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }

            reader.close();
        } catch (IOException e) {
            System.out.println("Помилка читання з файлу або файл порожній.");
        }
    }
}
