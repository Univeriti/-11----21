import java.io.FileReader;
import java.io.FileWriter;
import java.util.Scanner;

public class SimpleTextEditor {
    private static final String FILE_NAME = "textfile.txt";

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1. Записати у файл");
            System.out.println("2. Прочитати файл");
            System.out.println("3. Вийти");

            String choice = scanner.nextLine();

            if (choice.equals("1")) {
                writeToFile(scanner);
            } else if (choice.equals("2")) {
                readFromFile();
            } else if (choice.equals("3")) {
                System.out.println("До побачення!");
                break;
            } else {
                System.out.println("Невірний вибір. Спробуйте ще раз.");
            }
        }
    }

    private static void writeToFile(Scanner scanner) {
        System.out.print("Введіть текст: ");
        String text = scanner.nextLine();

        try {
            FileWriter writer = new FileWriter(FILE_NAME, true);
            writer.write(text + "");
            writer.close();
            System.out.println("Текст збережено.");
        } catch (Exception e) {
            System.out.println("Помилка запису у файл.");
        }
    }

    private static void readFromFile() {
        try {
            FileReader reader = new FileReader(FILE_NAME);
            int character;
            System.out.println("Вміст файлу:");
            while ((character = reader.read()) != -1) {
                System.out.print((char) character);
            }
            reader.close();
        } catch (Exception e) {
            System.out.println("Файл не знайдено або не можна прочитати.");
        }
    }
}
