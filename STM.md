==============================================================================
              SOFTWARE TESTING METHODOLOGIES (STM) - LAB RECORD               
==============================================================================

==============================================================================
Experiment 2: GUI Checkpoint for Single Property (Title/Text/Attribute)
==============================================================================

AIM:
  To perform a GUI checkpoint that verifies a single property (the title) of a window.

WHAT WE ARE DOING:
  1. A Swing JFrame is created with the title "Google" and displayed on screen.
  2. The expected title is stored and compared with the actual title read using getTitle().
  3. If both match, PASS is printed; otherwise FAIL is printed.
  4. This shows how a title/text/attribute checkpoint works in GUI testing.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
import javax.swing.JFrame;
public class program {
    public static void main(String[] args) throws InterruptedException {
        JFrame frame = new JFrame("Google");
        frame.setSize(400, 200);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLocationRelativeTo(null); frame.setVisible(true);
        String expectedTitle = "Google";
        String actualTitle = frame.getTitle();
        System.out.println("Actual Title : " + actualTitle);
        System.out.println("Expected Title : " + expectedTitle);
        if (actualTitle.equals(expectedTitle)) {
            System.out.println("PASS: Title is correct");
        } else {
            System.out.println("FAIL: Title is incorrect");
        }
        Thread.sleep(2000);
        frame.dispose();
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
Actual Title : Google
Expected Title : Google
PASS: Title is correct

==============================================================================
Experiment 3: GUI Checkpoint for Single Object/Window (Displayed/Enabled)
==============================================================================

AIM:
  To perform a GUI checkpoint on a single object by checking if it is displayed and enabled.

WHAT WE ARE DOING:
  1. A JFrame is created containing a "Search:" label and a text field (search box).
  2. After the window is shown, isShowing() checks whether the search box is displayed.
  3. isEnabled() checks whether the search box is enabled for user input.
  4. PASS is printed only if both are true, confirming the object is ready.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
import javax.swing.*;
public class program {
    public static void main(String[] args) throws InterruptedException
    {
        JFrame frame = new JFrame("Single Object Checkpoint");
        JTextField searchBox = new JTextField(20);
        JPanel panel = new JPanel();
        panel.add(new JLabel("Search:"));
        panel.add(searchBox);
        frame.add(panel);
        frame.setSize(400, 150);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLocationRelativeTo(null);
        frame.setVisible(true);
        Thread.sleep(500);
        boolean displayed = searchBox.isShowing();
        boolean enabled= searchBox.isEnabled();
        System.out.println("Displayed: " + displayed);
        System.out.println("Enabled : " + enabled);
        System.out.println(displayed && enabled
        ? "PASS: Search box is ready"
        : "FAIL: Search box is not ready");
        Thread.sleep(2000); frame.dispose();
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
Displayed: true
Enabled : true
PASS: Search box is ready

==============================================================================
Experiment 4(a): Bitmap Checkpoint for Object/Window (Screenshot Comparison)
==============================================================================

AIM:
  To perform a bitmap checkpoint by comparing a screenshot of an object with a stored baseline image.

WHAT WE ARE DOING:
  1. A JFrame with a search box is displayed and the search box alone is captured as an image.
  2. The image is saved as current_searchbox.png in the Screenshots folder.
  3. If no baseline exists, the user is told to rename it as the baseline; otherwise both images are compared pixel by pixel.
  4. Identical images give TEST PASS, any difference gives TEST FAIL.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
import javax.swing.*;
import javax.imageio.ImageIO;
import java.awt.*;
import java.awt.image.BufferedImage; import java.io.File;
public class NewTest {
    public static void main(String[] args) throws Exception {
        JFrame frame = new JFrame("Bitmap Checkpoint Test");
        JTextField searchBox = new JTextField("Search here", 20);
        JPanel panel = new JPanel();
        panel.add(searchBox);
        frame.add(panel);
        frame.setSize(350, 120);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLocationRelativeTo(null); frame.setVisible(true);
        Thread.sleep(1000);
        File folder = new File("Screenshots");
        if (!folder.exists()) folder.mkdir();
        BufferedImage currentImage = new BufferedImage( searchBox.getWidth(), searchBox.getHeight(),
        BufferedImage.TYPE_INT_RGB);
        Graphics2D g2 = currentImage.createGraphics();
        searchBox.paint(g2);
        g2.dispose();
        File currentFile = new File("Screenshots/current_searchbox.png");
        ImageIO.write(currentImage, "png", currentFile);
        System.out.println("Current screenshot saved:");
        System.out.println(currentFile.getAbsolutePath());
        File baselineFile = new File("Screenshots/baseline_searchbox.png");
        if (!baselineFile.exists()) {
            System.out.println("Baseline image not found.");
            System.out.println("Rename current_searchbox.png as baseline_searchbox.png");
        } else {
            boolean result = compareImages(baselineFile, currentFile);
            if (result) {
                System.out.println("BITMAP CHECKPOINT : TEST PASS");
                System.out.println("Images are identical.");
            } else {
                System.out.println("BITMAP CHECKPOINT : TEST FAIL");
                System.out.println("Images are different.");
            }
        }
        Thread.sleep(2000);
        frame.dispose();
    }
    public static boolean compareImages(File img1, File img2) throws Exception { BufferedImage image1 = ImageIO.read(img1);
        BufferedImage image2 = ImageIO.read(img2);
        if (image1.getWidth() != image2.getWidth() || image1.getHeight() != image2.getHeight())
        return false;
        for (int x = 0; x < image1.getWidth(); x++) {
            for (int y = 0; y < image1.getHeight(); y++) {
                if (image1.getRGB(x, y) != image2.getRGB(x, y))
                return false;
            }
        }
        return true;
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
Current screenshot saved:
C:\Users\DELL\Desktop\dsa_in_java\stm\Screenshots\current_searchbox.png
BITMAP CHECKPOINT : TEST PASS
Images are identical.

==============================================================================
Experiment 4(b): Bitmap Checkpoint for Screen Area (Crop + Compare)
==============================================================================

AIM:
  To perform a bitmap checkpoint on a screen area by cropping a region and comparing it with a baseline.

WHAT WE ARE DOING:
  1. A JFrame with a label, text field and Search button is displayed and the full window is captured.
  2. A fixed area (up to 800x600) is cropped and saved as current_google_area.png.
  3. The cropped image is compared with the baseline and a similarity percentage is calculated.
  4. A similarity of 95% or more is TEST PASS, otherwise TEST FAIL.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
import javax.swing.*;
import javax.imageio.ImageIO;
import java.awt.*;
import java.awt.image.BufferedImage;
import java.io.File;
public class NewTest {
    public static void main(String[] args) throws Exception {
        JFrame frame = new JFrame("Bitmap Area Checkpoint");
        JPanel panel = new JPanel(new FlowLayout());
        panel.add(new JLabel("Google Search"));
        panel.add(new JTextField(25));
        panel.add(new JButton("Search"));
        frame.add(panel);
        frame.setSize(800, 600);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLocationRelativeTo(null);
        frame.setVisible(true);
        Thread.sleep(1000);
        BufferedImage fullImage = new BufferedImage(frame.getWidth(), frame.getHeight(),
        BufferedImage.TYPE_INT_RGB);
        Graphics2D g2 = fullImage.createGraphics();
        frame.paint(g2);
        g2.dispose();
        File folder = new File("SeleniumScreenshots");
        if (!folder.exists())
        folder.mkdirs();
        int width = Math.min(800, fullImage.getWidth());
        int height = Math.min(600, fullImage.getHeight());
        BufferedImage currentArea = fullImage.getSubimage(0, 0, width, height);
        File currentFile = new File("SeleniumScreenshots/current_google_area.png");
        ImageIO.write(currentArea, "png", currentFile);
        System.out.println("Current screenshot saved:");
        System.out.println(currentFile.getAbsolutePath());
        File baselineFile = new File("SeleniumScreenshots/baseline_google_area.png");
        if (!baselineFile.exists()) {
            System.out.println("Baseline image not found.");
            System.out.println("Rename current_google_area.png to baseline_google_area.png");
        } else {
            BufferedImage baseline = ImageIO.read(baselineFile);
            double similarity = compareImages(baseline, currentArea);
            System.out.printf("Image Similarity : %.2f%%%n", similarity);
            if (similarity >= 95)
            System.out.println("BITMAP CHECKPOINT : TEST PASS");
            else
            System.out.println("BITMAP CHECKPOINT : TEST FAIL");
        }
        Thread.sleep(2000);
        frame.dispose();
    }
    public static double compareImages(BufferedImage img1, BufferedImage img2) {
        if (img1.getWidth() != img2.getWidth() ||
        img1.getHeight() != img2.getHeight()) return 0;
        long totalPixels = (long) img1.getWidth() * img1.getHeight();
        long samePixels = 0;
        for (int x = 0; x < img1.getWidth(); x++) {
            for (int y = 0; y < img1.getHeight(); y++) {
                if (img1.getRGB(x, y) == img2.getRGB(x, y)) samePixels++;
            }
        }
        return ((double) samePixels / totalPixels) * 100;
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
Current screenshot saved:
C:\Users\DELL\Desktop\dsa_in_java\stm\SeleniumScreenshots\current_google_area.png
Image Similarity : 100.00%
BITMAP CHECKPOINT : TEST PASS

==============================================================================
Experiment 5: Database Checkpoint – Default Check (Record Exists)
==============================================================================

AIM:
  To perform a database checkpoint (default check) that verifies a record exists in a table.

WHAT WE ARE DOING:
  1. A connection is made to an H2 database and a STUDENT table is created.
  2. Old data is cleared and one record (1, Ajay, ajay@gmail.com) is inserted.
  3. A SELECT query searches for the record with ID = 1.
  4. If found, its details are printed with TEST PASSED; otherwise TEST FAILED is printed.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;
public class NewTest {
    public static void main(String[] args) {
        try {
            Connection con = DriverManager.getConnection( "jdbc:h2:./StudentDB", "sa", "");
            Statement stmt = con.createStatement();
            stmt.execute("CREATE TABLE IF NOT EXISTS STUDENT (" + "ID INT PRIMARY KEY, " +
            "NAME VARCHAR(50), " + "EMAIL VARCHAR(100))");
            stmt.execute("DELETE FROM STUDENT");
            stmt.executeUpdate("INSERT INTO STUDENT VALUES " +
            "(1, 'Ajay', 'ajay@gmail.com')");
            ResultSet rs = stmt.executeQuery(
            "SELECT * FROM STUDENT WHERE ID = 1");
            if (rs.next()) {
                System.out.println("Record Exists");
                System.out.println("ID : " + rs.getInt("ID"));
                System.out.println("Name : " + rs.getString("NAME"));
                System.out.println("Email : " + rs.getString("EMAIL"));
                System.out.println("TEST PASSED");
            } else {
                System.out.println("Record Not Found");
                System.out.println("TEST FAILED");
            }
            rs.close();
            stmt.close();
            con.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
PS C:\Users\DELL\Desktop\dsa_in_java\stm> javac -cp ".;lib\h2-2.5.252.jar" NewTest.java
PS C:\Users\DELL\Desktop\dsa_in_java\stm> java -cp ".;lib\h2-2.5.252.jar" NewTest
Record Exists
ID : 1
Name : Ajay
Email : ajay@gmail.com
TEST PASSED

==============================================================================
Experiment 6: Database Checkpoint – Custom Check (Validate Specific Value)
==============================================================================

AIM:
  To perform a database checkpoint (custom check) that validates a specific derived value from the database.

WHAT WE ARE DOING:
  1. A students table is created in an H2 database with three records (id, name, marks).
  2. The marks of a given student are read using a PreparedStatement.
  3. Status is calculated as Pass (marks >= 50) or Fail, and compared with the expected status.
  4. A matching status prints PASS, otherwise FAIL (also FAIL if the record is missing).

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
import java.sql.*;
public class DatabaseCheckpointCustomCheck {
    static final String DB_URL = "jdbc:h2:./student";
    public static void setupDatabase() throws SQLException {
        try (Connection conn = DriverManager.getConnection(DB_URL);
        Statement stmt = conn.createStatement()) {
            stmt.execute("CREATE TABLE IF NOT EXISTS students (" +
            "id INTEGER PRIMARY KEY, name VARCHAR(50), marks INTEGER)");
            stmt.execute("DELETE FROM students");
            stmt.execute("INSERT INTO students VALUES (1, 'Amit', 78)");
            stmt.execute("INSERT INTO students VALUES (2, 'Neha', 45)");
            stmt.execute("INSERT INTO students VALUES (3, 'Ravi', 92)");
        }
    }
    public static boolean customCheckpoint(int studentId, String expectedStatus)
    throws SQLException {
        try (Connection conn = DriverManager.getConnection(DB_URL);
        PreparedStatement ps = conn.prepareStatement(
        "SELECT marks FROM students WHERE id = ?")) {
            ps.setInt(1, studentId);
            ResultSet rs = ps.executeQuery();
            if (!rs.next()) {
                System.out.println("FAIL: No record found for id " + studentId);
                return false;
            }
            int marks = rs.getInt("marks");
            String actualStatus = (marks >= 50) ? "Pass" : "Fail";
            if (actualStatus.equals(expectedStatus)) {
                System.out.println("PASS: Student " + studentId +
                " status = " + actualStatus +
                " (Custom check matched)");
                return true;
            } else {
                System.out.println("FAIL: Student " + studentId +
                " expected " + expectedStatus +
                ", got " + actualStatus);
                return false;
            }
        }
    }
    public static void main(String[] args) throws Exception {
        setupDatabase();
        customCheckpoint(1, "Pass");
        customCheckpoint(2, "Fail");
        customCheckpoint(3, "Pass");
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
PS C:\Users\DELL\Desktop\dsa_in_java\stm> javac -cp ".;lib\h2-2.5.252.jar" DatabaseCheckpointCustomCheck.java
PS C:\Users\DELL\Desktop\dsa_in_java\stm> java -cp ".;lib\h2-2.5.252.jar" DatabaseCheckpointCustomCheck
PASS: Student 1 status = Pass (Custom check matched)
PASS: Student 2 status = Fail (Custom check matched)
PASS: Student 3 status = Pass (Custom check matched)

==============================================================================
Experiment 7(a): Data Driven Test – Dynamic Test Data Submission
==============================================================================

AIM:
  To perform data driven testing using dynamically generated (random) test data.

WHAT WE ARE DOING:
  1. A discount function gives 10% off for electronics, 20% off for clothing and no discount otherwise.
  2. Five test cases are generated using random prices (100 to 1000) and random categories.
  3. Each case is passed to the function and the discounted price is printed.
  4. This shows that test data can be created at run time instead of being fixed.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
import java.util.Random;
public class DynamicDataTest {
    public static double calculateDiscount(double price, String category) { switch (category) {
            case "electronics": return price * 0.9; case "clothing": return price * 0.8; default: return price;
        }
    }
    public static void main(String[] args) {
        String[] categories = {"electronics", "clothing", "grocery"}; Random rand = new Random();
        System.out.println("---- Dynamic Test Data Submission ");
        for (int i = 1; i <= 5; i++) {
            int price = 100 + rand.nextInt(901);
            String category = categories[rand.nextInt(categories.length)];
            double result = calculateDiscount(price, category);
            System.out.printf(
            "Test %d: price=%d, category=%s -> discounted=%.2f%n", i, price, category, result);
        }
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
---- Dynamic Test Data Submission
Test 1: price=755, category=grocery -> discounted=755.00
Test 2: price=784, category=clothing -> discounted=627.20
Test 3: price=591, category=electronics -> discounted=531.90
Test 4: price=419, category=electronics -> discounted=377.10
Test 5: price=277, category=clothing -> discounted=221.60
PS C:\Users\DELL\Desktop\dsa_in_java\stm>

==============================================================================
Experiment 7(b): Data Driven Test – Through Flat Files (CSV/TXT)
==============================================================================

AIM:
  To perform data driven testing by reading test data from a flat file (TXT/CSV).

WHAT WE ARE DOING:
  1. A file testdata.txt is created with lines in the form price,category.
  2. The program reads the file line by line and splits each line into price and category.
  3. Each pair is passed to the discount function and the result is printed.
  4. This separates test data from test code so data can be changed without editing the program.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
import java.io.*;
public class FlatFileTest {
    public static double calculateDiscount(double price, String category) { switch (category) {
            case "electronics": return price * 0.9; case "clothing": return price * 0.8; default: return price;
        }
    }
    public static void createFlatFile() throws IOException {
        try (PrintWriter pw = new PrintWriter(new FileWriter("testdata.txt")))
        {
            pw.println("500,electronics");
            pw.println("300,clothing"); pw.println("150,grocery");
        }
    }
    public static void flatFileTest() throws IOException {
        System.out.println("---- Data Driven Test via Flat File ");
        try (BufferedReader br = new BufferedReader( new FileReader("testdata.txt")))
        {
            String line;
            while ((line = br.readLine()) != null) { String[] parts = line.split(",");
                double price = Double.parseDouble(parts[0]); String category = parts[1];
                double result = calculateDiscount(price, category);
                System.out.printf(
                "price=%.1f, category=%s -> discounted=%.2f%n", price, category, result);
            }
        }
    }
    public static void main(String[] args) throws IOException { createFlatFile();
        flatFileTest();
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
Compile / Run Commands
javac FlatFileTest.java
java FlatFileTest
Output
---- Data Driven Test via Flat File ----
price=500.0, category=electronics -> discounted=450.00
price=300.0, category=clothing -> discounted=240.00
price=150.0, category=grocery -> discounted=150.0

==============================================================================
Experiment 7(c): Data Driven Test – Through Front Grids (Web Tables)
==============================================================================

AIM:
  To perform data driven testing through a front-end grid (table) that displays the test data and results.

WHAT WE ARE DOING:
  1. Test data (price and category) is stored in a grid-like array.
  2. For each row, the discount function is called to compute the result.
  3. The rows are added to a Swing JTable with columns Price, Category and Result.
  4. The table is shown in a window so the inputs and outputs can be viewed together.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
import javax.swing.*;
import javax.swing.table.DefaultTableModel;
public class FrontEndGridTest {
    public static double calculateDiscount(double price, String category) { switch (category) {
            case "electronics": return price * 0.9; case "clothing": return price * 0.8; default: return price;
        }
    }
    public static void main(String[] args) {
        JFrame frame = new JFrame("Front End Grid - Data Driven Test");
        String[] columns = {"Price", "Category", "Result"};
        DefaultTableModel model = new DefaultTableModel(columns, 0);
        Object[][] gridData = {
            {500.0, "electronics"},
            {300.0, "clothing"},
            {150.0, "grocery"}
        };
        for (Object[] row : gridData) { double price = (double) row[0];
            String category = (String) row[1];
            double result = calculateDiscount(price, category);
            model.addRow(new Object[]{
                price, category, String.format("%.2f", result)});
        }
        JTable table = new JTable(model);
        frame.add(new JScrollPane(table));
        frame.setSize(400, 200);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
Compile / Run Commands
javac FrontEndGridTest.java
java FrontEndGridTest
Output
Price Category Result
500.0 electronics 450.00
300.0 clothing 240.00
150.0 grocery 150.00

##############################################################################
                                   WEEK 10                                    
##############################################################################

==============================================================================
Experiment 7(e): Batch Testing – Without Parameter Passing (Suite Run)
==============================================================================

AIM:
  To perform batch testing without parameter passing, running several fixed tests as one suite.

WHAT WE ARE DOING:
  1. Two test methods are written: testAddition and testSubtraction.
  2. Each method checks a fixed condition using assert and prints PASS.
  3. The main method runs all the tests one after another as a batch.
  4. No data is passed to the tests; each test has its values written inside it.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
public class BatchNoParams {
    public static void testAddition() {
        assert 2 + 3 == 5;
        System.out.println("test_addition: PASS");
    }
    public static void testSubtraction() { assert 5 - 2 == 3;
        System.out.println("test_subtraction: PASS");
    }
    public static void main(String[] args) {
        System.out.println("---- Batch Testing (No Parameters) ");
        testAddition(); testSubtraction();
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
---- Batch Testing (No Parameters)
test_addition: PASS
test_subtraction: PASS

==============================================================================
Experiment 7(f): Batch Testing – With Parameter Passing (Suite Parameters)
==============================================================================

AIM:
  To perform batch testing with parameter passing, running one test method with many sets of values.

WHAT WE ARE DOING:
  1. A single testOperation method accepts two numbers, an operator and the expected result.
  2. A list of test cases is stored in an array and passed to the method in a loop.
  3. The actual result is compared with the expected one and PASS or FAIL is printed for each case.
  4. One deliberately wrong case (5 - 5 expected 1) shows how a FAIL is reported.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
public class BatchWithParams {
    static void testOperation(int a, int b, char op, int expected) {
        int result = 0;
        switch (op) {
            case '+': result = a + b;
            break;
            case '-': result = a - b;
            break;
            case '*': result = a * b;
            break;
        }
        String status = (result == expected) ? "PASS" : "FAIL";
        System.out.printf("Test: %d %c %d = %d (expected %d) -> %s%n", a, op, b, result, expected, status);
    }
    public static void main(String[] args) {
        int[][] testCases = {{2, 3, '+', 5},{10, 4, '-', 6},{3, 3, '*', 9},{5, 5, '-', 1}};
        System.out.println("---- Batch Testing (With Parameters) ");
        for (int[] tc : testCases) {
            testOperation(tc[0], tc[1], (char) tc[2], tc[3]);
        }
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
---- Batch Testing (With Parameters)
Test: 2 + 3 = 5 (expected 5) -> PASS
Test: 10 - 4 = 6 (expected 6) -> PASS
Test: 3 * 3 = 9 (expected 9) -> PASS
Test: 5 - 5 = 0 (expected 1) -> FAIL

==============================================================================
Experiment 8: Data Driven Batch (Batch + Multiple Data Sets)
==============================================================================

AIM:
  To perform a data driven batch test, running a batch of tests using multiple data sets from a CSV file.

WHAT WE ARE DOING:
  1. A CSV file batch_data.csv is created with Price, Category and ExpectedResult columns.
  2. Each row is read, the discount is calculated and compared with the expected result.
  3. PASS or FAIL is printed for every row.
  4. A final summary shows the total number of tests passed and failed.

------------------------------------------------------------------------------
PROGRAM:
------------------------------------------------------------------------------
import java.io.*;
public class DataDrivenBatch {
    public static double calculateDiscount(double price, String category) {
        switch (category) {
            case "electronics":
            return price * 0.9;
            case "clothing":
            return price * 0.8;
            default:
            return price;
        }
    }
    public static void createCsvFile() throws IOException {
        try (PrintWriter pw = new PrintWriter(new FileWriter("batch_data.csv"))) {
            pw.println("Price,Category,ExpectedResult");
            pw.println("500,electronics,450");
            pw.println("300,clothing,240");
            pw.println("150,grocery,150");
            pw.println("1000,electronics,900");
        }
    }
    public static void dataDrivenBatch() throws IOException {
        System.out.println("---- Data Driven Batch Test");
        int passCount = 0;
        int failCount = 0;
        try (BufferedReader br = new BufferedReader(new FileReader("batch_data.csv"))) {
            String line = br.readLine();
            while ((line = br.readLine()) != null) {
                String[] parts = line.split(",");
                double price = Double.parseDouble(parts[0]);
                String category = parts[1];
                double expected = Double.parseDouble(parts[2]);
                double actual = calculateDiscount(price, category);
                if (actual == expected) {
                    System.out.printf("PASS: %s, price=%.1f -> %.1f%n",
                    category, price, actual);
                    passCount++;
                } else {
                    System.out.printf("FAIL: %s, price=%.1f -> got %.1f, expected %.1f%n",
                    category, price, actual, expected);
                    failCount++;
                }
            }
        }
        System.out.println("\nBatch Summary: " + passCount +
        " Passed, " + failCount + " Failed");
    }
    public static void main(String[] args) throws IOException {
        createCsvFile();
        dataDrivenBatch();
    }
}

------------------------------------------------------------------------------
OUTPUT:
------------------------------------------------------------------------------
---- Data Driven Batch Test
PASS: electronics, price=500.0 -> 450.0
PASS: clothing, price=300.0 -> 240.0
PASS: grocery, price=150.0 -> 150.0
PASS: electronics, price=1000.0 -> 900.0
Batch Summary: 4 Passed, 0 Failed
