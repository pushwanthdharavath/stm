==============================================================================

&#x20;             SOFTWARE TESTING METHODOLOGIES (STM) - LAB RECORD               

==============================================================================



==============================================================================

Experiment 2: GUI Checkpoint for Single Property (Title/Text/Attribute)

==============================================================================



AIM:

&#x20; To perform a GUI checkpoint that verifies a single property (the title) of a window.



WHAT WE ARE DOING:

&#x20; 1. A Swing JFrame is created with the title "Google" and displayed on screen.

&#x20; 2. The expected title is stored and compared with the actual title read using getTitle().

&#x20; 3. If both match, PASS is printed; otherwise FAIL is printed.

&#x20; 4. This shows how a title/text/attribute checkpoint works in GUI testing.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

import javax.swing.JFrame;

public class program {

&#x20;   public static void main(String\[] args) throws InterruptedException {

&#x20;       JFrame frame = new JFrame("Google");

&#x20;       frame.setSize(400, 200);

&#x20;       frame.setDefaultCloseOperation(JFrame.EXIT\_ON\_CLOSE);

&#x20;       frame.setLocationRelativeTo(null); frame.setVisible(true);

&#x20;       String expectedTitle = "Google";

&#x20;       String actualTitle = frame.getTitle();

&#x20;       System.out.println("Actual Title : " + actualTitle);

&#x20;       System.out.println("Expected Title : " + expectedTitle);

&#x20;       if (actualTitle.equals(expectedTitle)) {

&#x20;           System.out.println("PASS: Title is correct");

&#x20;       } else {

&#x20;           System.out.println("FAIL: Title is incorrect");

&#x20;       }

&#x20;       Thread.sleep(2000);

&#x20;       frame.dispose();

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

Actual Title : Google

Expected Title : Google

PASS: Title is correct



==============================================================================

Experiment 3: GUI Checkpoint for Single Object/Window (Displayed/Enabled)

==============================================================================



AIM:

&#x20; To perform a GUI checkpoint on a single object by checking if it is displayed and enabled.



WHAT WE ARE DOING:

&#x20; 1. A JFrame is created containing a "Search:" label and a text field (search box).

&#x20; 2. After the window is shown, isShowing() checks whether the search box is displayed.

&#x20; 3. isEnabled() checks whether the search box is enabled for user input.

&#x20; 4. PASS is printed only if both are true, confirming the object is ready.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

import javax.swing.\*;

public class program {

&#x20;   public static void main(String\[] args) throws InterruptedException

&#x20;   {

&#x20;       JFrame frame = new JFrame("Single Object Checkpoint");

&#x20;       JTextField searchBox = new JTextField(20);

&#x20;       JPanel panel = new JPanel();

&#x20;       panel.add(new JLabel("Search:"));

&#x20;       panel.add(searchBox);

&#x20;       frame.add(panel);

&#x20;       frame.setSize(400, 150);

&#x20;       frame.setDefaultCloseOperation(JFrame.EXIT\_ON\_CLOSE);

&#x20;       frame.setLocationRelativeTo(null);

&#x20;       frame.setVisible(true);

&#x20;       Thread.sleep(500);

&#x20;       boolean displayed = searchBox.isShowing();

&#x20;       boolean enabled= searchBox.isEnabled();

&#x20;       System.out.println("Displayed: " + displayed);

&#x20;       System.out.println("Enabled : " + enabled);

&#x20;       System.out.println(displayed \&\& enabled

&#x20;       ? "PASS: Search box is ready"

&#x20;       : "FAIL: Search box is not ready");

&#x20;       Thread.sleep(2000); frame.dispose();

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

Displayed: true

Enabled : true

PASS: Search box is ready



==============================================================================

Experiment 4(a): Bitmap Checkpoint for Object/Window (Screenshot Comparison)

==============================================================================



AIM:

&#x20; To perform a bitmap checkpoint by comparing a screenshot of an object with a stored baseline image.



WHAT WE ARE DOING:

&#x20; 1. A JFrame with a search box is displayed and the search box alone is captured as an image.

&#x20; 2. The image is saved as current\_searchbox.png in the Screenshots folder.

&#x20; 3. If no baseline exists, the user is told to rename it as the baseline; otherwise both images are compared pixel by pixel.

&#x20; 4. Identical images give TEST PASS, any difference gives TEST FAIL.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

import javax.swing.\*;

import javax.imageio.ImageIO;

import java.awt.\*;

import java.awt.image.BufferedImage; import java.io.File;

public class NewTest {

&#x20;   public static void main(String\[] args) throws Exception {

&#x20;       JFrame frame = new JFrame("Bitmap Checkpoint Test");

&#x20;       JTextField searchBox = new JTextField("Search here", 20);

&#x20;       JPanel panel = new JPanel();

&#x20;       panel.add(searchBox);

&#x20;       frame.add(panel);

&#x20;       frame.setSize(350, 120);

&#x20;       frame.setDefaultCloseOperation(JFrame.EXIT\_ON\_CLOSE);

&#x20;       frame.setLocationRelativeTo(null); frame.setVisible(true);

&#x20;       Thread.sleep(1000);

&#x20;       File folder = new File("Screenshots");

&#x20;       if (!folder.exists()) folder.mkdir();

&#x20;       BufferedImage currentImage = new BufferedImage( searchBox.getWidth(), searchBox.getHeight(),

&#x20;       BufferedImage.TYPE\_INT\_RGB);

&#x20;       Graphics2D g2 = currentImage.createGraphics();

&#x20;       searchBox.paint(g2);

&#x20;       g2.dispose();

&#x20;       File currentFile = new File("Screenshots/current\_searchbox.png");

&#x20;       ImageIO.write(currentImage, "png", currentFile);

&#x20;       System.out.println("Current screenshot saved:");

&#x20;       System.out.println(currentFile.getAbsolutePath());

&#x20;       File baselineFile = new File("Screenshots/baseline\_searchbox.png");

&#x20;       if (!baselineFile.exists()) {

&#x20;           System.out.println("Baseline image not found.");

&#x20;           System.out.println("Rename current\_searchbox.png as baseline\_searchbox.png");

&#x20;       } else {

&#x20;           boolean result = compareImages(baselineFile, currentFile);

&#x20;           if (result) {

&#x20;               System.out.println("BITMAP CHECKPOINT : TEST PASS");

&#x20;               System.out.println("Images are identical.");

&#x20;           } else {

&#x20;               System.out.println("BITMAP CHECKPOINT : TEST FAIL");

&#x20;               System.out.println("Images are different.");

&#x20;           }

&#x20;       }

&#x20;       Thread.sleep(2000);

&#x20;       frame.dispose();

&#x20;   }

&#x20;   public static boolean compareImages(File img1, File img2) throws Exception { BufferedImage image1 = ImageIO.read(img1);

&#x20;       BufferedImage image2 = ImageIO.read(img2);

&#x20;       if (image1.getWidth() != image2.getWidth() || image1.getHeight() != image2.getHeight())

&#x20;       return false;

&#x20;       for (int x = 0; x < image1.getWidth(); x++) {

&#x20;           for (int y = 0; y < image1.getHeight(); y++) {

&#x20;               if (image1.getRGB(x, y) != image2.getRGB(x, y))

&#x20;               return false;

&#x20;           }

&#x20;       }

&#x20;       return true;

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

Current screenshot saved:

C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm\\Screenshots\\current\_searchbox.png

BITMAP CHECKPOINT : TEST PASS

Images are identical.



==============================================================================

Experiment 4(b): Bitmap Checkpoint for Screen Area (Crop + Compare)

==============================================================================



AIM:

&#x20; To perform a bitmap checkpoint on a screen area by cropping a region and comparing it with a baseline.



WHAT WE ARE DOING:

&#x20; 1. A JFrame with a label, text field and Search button is displayed and the full window is captured.

&#x20; 2. A fixed area (up to 800x600) is cropped and saved as current\_google\_area.png.

&#x20; 3. The cropped image is compared with the baseline and a similarity percentage is calculated.

&#x20; 4. A similarity of 95% or more is TEST PASS, otherwise TEST FAIL.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

import javax.swing.\*;

import javax.imageio.ImageIO;

import java.awt.\*;

import java.awt.image.BufferedImage;

import java.io.File;

public class NewTest {

&#x20;   public static void main(String\[] args) throws Exception {

&#x20;       JFrame frame = new JFrame("Bitmap Area Checkpoint");

&#x20;       JPanel panel = new JPanel(new FlowLayout());

&#x20;       panel.add(new JLabel("Google Search"));

&#x20;       panel.add(new JTextField(25));

&#x20;       panel.add(new JButton("Search"));

&#x20;       frame.add(panel);

&#x20;       frame.setSize(800, 600);

&#x20;       frame.setDefaultCloseOperation(JFrame.EXIT\_ON\_CLOSE);

&#x20;       frame.setLocationRelativeTo(null);

&#x20;       frame.setVisible(true);

&#x20;       Thread.sleep(1000);

&#x20;       BufferedImage fullImage = new BufferedImage(frame.getWidth(), frame.getHeight(),

&#x20;       BufferedImage.TYPE\_INT\_RGB);

&#x20;       Graphics2D g2 = fullImage.createGraphics();

&#x20;       frame.paint(g2);

&#x20;       g2.dispose();

&#x20;       File folder = new File("SeleniumScreenshots");

&#x20;       if (!folder.exists())

&#x20;       folder.mkdirs();

&#x20;       int width = Math.min(800, fullImage.getWidth());

&#x20;       int height = Math.min(600, fullImage.getHeight());

&#x20;       BufferedImage currentArea = fullImage.getSubimage(0, 0, width, height);

&#x20;       File currentFile = new File("SeleniumScreenshots/current\_google\_area.png");

&#x20;       ImageIO.write(currentArea, "png", currentFile);

&#x20;       System.out.println("Current screenshot saved:");

&#x20;       System.out.println(currentFile.getAbsolutePath());

&#x20;       File baselineFile = new File("SeleniumScreenshots/baseline\_google\_area.png");

&#x20;       if (!baselineFile.exists()) {

&#x20;           System.out.println("Baseline image not found.");

&#x20;           System.out.println("Rename current\_google\_area.png to baseline\_google\_area.png");

&#x20;       } else {

&#x20;           BufferedImage baseline = ImageIO.read(baselineFile);

&#x20;           double similarity = compareImages(baseline, currentArea);

&#x20;           System.out.printf("Image Similarity : %.2f%%%n", similarity);

&#x20;           if (similarity >= 95)

&#x20;           System.out.println("BITMAP CHECKPOINT : TEST PASS");

&#x20;           else

&#x20;           System.out.println("BITMAP CHECKPOINT : TEST FAIL");

&#x20;       }

&#x20;       Thread.sleep(2000);

&#x20;       frame.dispose();

&#x20;   }

&#x20;   public static double compareImages(BufferedImage img1, BufferedImage img2) {

&#x20;       if (img1.getWidth() != img2.getWidth() ||

&#x20;       img1.getHeight() != img2.getHeight()) return 0;

&#x20;       long totalPixels = (long) img1.getWidth() \* img1.getHeight();

&#x20;       long samePixels = 0;

&#x20;       for (int x = 0; x < img1.getWidth(); x++) {

&#x20;           for (int y = 0; y < img1.getHeight(); y++) {

&#x20;               if (img1.getRGB(x, y) == img2.getRGB(x, y)) samePixels++;

&#x20;           }

&#x20;       }

&#x20;       return ((double) samePixels / totalPixels) \* 100;

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

Current screenshot saved:

C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm\\SeleniumScreenshots\\current\_google\_area.png

Image Similarity : 100.00%

BITMAP CHECKPOINT : TEST PASS



==============================================================================

Experiment 5: Database Checkpoint – Default Check (Record Exists)

==============================================================================



AIM:

&#x20; To perform a database checkpoint (default check) that verifies a record exists in a table.



WHAT WE ARE DOING:

&#x20; 1. A connection is made to an H2 database and a STUDENT table is created.

&#x20; 2. Old data is cleared and one record (1, Ajay, ajay@gmail.com) is inserted.

&#x20; 3. A SELECT query searches for the record with ID = 1.

&#x20; 4. If found, its details are printed with TEST PASSED; otherwise TEST FAILED is printed.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

import java.sql.Connection;

import java.sql.DriverManager;

import java.sql.ResultSet;

import java.sql.Statement;

public class NewTest {

&#x20;   public static void main(String\[] args) {

&#x20;       try {

&#x20;           Connection con = DriverManager.getConnection( "jdbc:h2:./StudentDB", "sa", "");

&#x20;           Statement stmt = con.createStatement();

&#x20;           stmt.execute("CREATE TABLE IF NOT EXISTS STUDENT (" + "ID INT PRIMARY KEY, " +

&#x20;           "NAME VARCHAR(50), " + "EMAIL VARCHAR(100))");

&#x20;           stmt.execute("DELETE FROM STUDENT");

&#x20;           stmt.executeUpdate("INSERT INTO STUDENT VALUES " +

&#x20;           "(1, 'Ajay', 'ajay@gmail.com')");

&#x20;           ResultSet rs = stmt.executeQuery(

&#x20;           "SELECT \* FROM STUDENT WHERE ID = 1");

&#x20;           if (rs.next()) {

&#x20;               System.out.println("Record Exists");

&#x20;               System.out.println("ID : " + rs.getInt("ID"));

&#x20;               System.out.println("Name : " + rs.getString("NAME"));

&#x20;               System.out.println("Email : " + rs.getString("EMAIL"));

&#x20;               System.out.println("TEST PASSED");

&#x20;           } else {

&#x20;               System.out.println("Record Not Found");

&#x20;               System.out.println("TEST FAILED");

&#x20;           }

&#x20;           rs.close();

&#x20;           stmt.close();

&#x20;           con.close();

&#x20;       } catch (Exception e) {

&#x20;           e.printStackTrace();

&#x20;       }

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

PS C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm> javac -cp ".;lib\\h2-2.5.252.jar" NewTest.java

PS C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm> java -cp ".;lib\\h2-2.5.252.jar" NewTest

Record Exists

ID : 1

Name : Ajay

Email : ajay@gmail.com

TEST PASSED



==============================================================================

Experiment 6: Database Checkpoint – Custom Check (Validate Specific Value)

==============================================================================



AIM:

&#x20; To perform a database checkpoint (custom check) that validates a specific derived value from the database.



WHAT WE ARE DOING:

&#x20; 1. A students table is created in an H2 database with three records (id, name, marks).

&#x20; 2. The marks of a given student are read using a PreparedStatement.

&#x20; 3. Status is calculated as Pass (marks >= 50) or Fail, and compared with the expected status.

&#x20; 4. A matching status prints PASS, otherwise FAIL (also FAIL if the record is missing).



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

import java.sql.\*;

public class DatabaseCheckpointCustomCheck {

&#x20;   static final String DB\_URL = "jdbc:h2:./student";

&#x20;   public static void setupDatabase() throws SQLException {

&#x20;       try (Connection conn = DriverManager.getConnection(DB\_URL);

&#x20;       Statement stmt = conn.createStatement()) {

&#x20;           stmt.execute("CREATE TABLE IF NOT EXISTS students (" +

&#x20;           "id INTEGER PRIMARY KEY, name VARCHAR(50), marks INTEGER)");

&#x20;           stmt.execute("DELETE FROM students");

&#x20;           stmt.execute("INSERT INTO students VALUES (1, 'Amit', 78)");

&#x20;           stmt.execute("INSERT INTO students VALUES (2, 'Neha', 45)");

&#x20;           stmt.execute("INSERT INTO students VALUES (3, 'Ravi', 92)");

&#x20;       }

&#x20;   }

&#x20;   public static boolean customCheckpoint(int studentId, String expectedStatus)

&#x20;   throws SQLException {

&#x20;       try (Connection conn = DriverManager.getConnection(DB\_URL);

&#x20;       PreparedStatement ps = conn.prepareStatement(

&#x20;       "SELECT marks FROM students WHERE id = ?")) {

&#x20;           ps.setInt(1, studentId);

&#x20;           ResultSet rs = ps.executeQuery();

&#x20;           if (!rs.next()) {

&#x20;               System.out.println("FAIL: No record found for id " + studentId);

&#x20;               return false;

&#x20;           }

&#x20;           int marks = rs.getInt("marks");

&#x20;           String actualStatus = (marks >= 50) ? "Pass" : "Fail";

&#x20;           if (actualStatus.equals(expectedStatus)) {

&#x20;               System.out.println("PASS: Student " + studentId +

&#x20;               " status = " + actualStatus +

&#x20;               " (Custom check matched)");

&#x20;               return true;

&#x20;           } else {

&#x20;               System.out.println("FAIL: Student " + studentId +

&#x20;               " expected " + expectedStatus +

&#x20;               ", got " + actualStatus);

&#x20;               return false;

&#x20;           }

&#x20;       }

&#x20;   }

&#x20;   public static void main(String\[] args) throws Exception {

&#x20;       setupDatabase();

&#x20;       customCheckpoint(1, "Pass");

&#x20;       customCheckpoint(2, "Fail");

&#x20;       customCheckpoint(3, "Pass");

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

PS C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm> javac -cp ".;lib\\h2-2.5.252.jar" DatabaseCheckpointCustomCheck.java

PS C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm> java -cp ".;lib\\h2-2.5.252.jar" DatabaseCheckpointCustomCheck

PASS: Student 1 status = Pass (Custom check matched)

PASS: Student 2 status = Fail (Custom check matched)

PASS: Student 3 status = Pass (Custom check matched)



==============================================================================

Experiment 7(a): Data Driven Test – Dynamic Test Data Submission

==============================================================================



AIM:

&#x20; To perform data driven testing using dynamically generated (random) test data.



WHAT WE ARE DOING:

&#x20; 1. A discount function gives 10% off for electronics, 20% off for clothing and no discount otherwise.

&#x20; 2. Five test cases are generated using random prices (100 to 1000) and random categories.

&#x20; 3. Each case is passed to the function and the discounted price is printed.

&#x20; 4. This shows that test data can be created at run time instead of being fixed.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

import java.util.Random;

public class DynamicDataTest {

&#x20;   public static double calculateDiscount(double price, String category) { switch (category) {

&#x20;           case "electronics": return price \* 0.9; case "clothing": return price \* 0.8; default: return price;

&#x20;       }

&#x20;   }

&#x20;   public static void main(String\[] args) {

&#x20;       String\[] categories = {"electronics", "clothing", "grocery"}; Random rand = new Random();

&#x20;       System.out.println("---- Dynamic Test Data Submission ");

&#x20;       for (int i = 1; i <= 5; i++) {

&#x20;           int price = 100 + rand.nextInt(901);

&#x20;           String category = categories\[rand.nextInt(categories.length)];

&#x20;           double result = calculateDiscount(price, category);

&#x20;           System.out.printf(

&#x20;           "Test %d: price=%d, category=%s -> discounted=%.2f%n", i, price, category, result);

&#x20;       }

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

\---- Dynamic Test Data Submission

Test 1: price=755, category=grocery -> discounted=755.00

Test 2: price=784, category=clothing -> discounted=627.20

Test 3: price=591, category=electronics -> discounted=531.90

Test 4: price=419, category=electronics -> discounted=377.10

Test 5: price=277, category=clothing -> discounted=221.60

PS C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm>



==============================================================================

Experiment 7(b): Data Driven Test – Through Flat Files (CSV/TXT)

==============================================================================



AIM:

&#x20; To perform data driven testing by reading test data from a flat file (TXT/CSV).



WHAT WE ARE DOING:

&#x20; 1. A file testdata.txt is created with lines in the form price,category.

&#x20; 2. The program reads the file line by line and splits each line into price and category.

&#x20; 3. Each pair is passed to the discount function and the result is printed.

&#x20; 4. This separates test data from test code so data can be changed without editing the program.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

import java.io.\*;

public class FlatFileTest {

&#x20;   public static double calculateDiscount(double price, String category) { switch (category) {

&#x20;           case "electronics": return price \* 0.9; case "clothing": return price \* 0.8; default: return price;

&#x20;       }

&#x20;   }

&#x20;   public static void createFlatFile() throws IOException {

&#x20;       try (PrintWriter pw = new PrintWriter(new FileWriter("testdata.txt")))

&#x20;       {

&#x20;           pw.println("500,electronics");

&#x20;           pw.println("300,clothing"); pw.println("150,grocery");

&#x20;       }

&#x20;   }

&#x20;   public static void flatFileTest() throws IOException {

&#x20;       System.out.println("---- Data Driven Test via Flat File ");

&#x20;       try (BufferedReader br = new BufferedReader( new FileReader("testdata.txt")))

&#x20;       {

&#x20;           String line;

&#x20;           while ((line = br.readLine()) != null) { String\[] parts = line.split(",");

&#x20;               double price = Double.parseDouble(parts\[0]); String category = parts\[1];

&#x20;               double result = calculateDiscount(price, category);

&#x20;               System.out.printf(

&#x20;               "price=%.1f, category=%s -> discounted=%.2f%n", price, category, result);

&#x20;           }

&#x20;       }

&#x20;   }

&#x20;   public static void main(String\[] args) throws IOException { createFlatFile();

&#x20;       flatFileTest();

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

Compile / Run Commands

javac FlatFileTest.java

java FlatFileTest

Output

\---- Data Driven Test via Flat File ----

price=500.0, category=electronics -> discounted=450.00

price=300.0, category=clothing -> discounted=240.00

price=150.0, category=grocery -> discounted=150.0



==============================================================================

Experiment 7(c): Data Driven Test – Through Front Grids (Web Tables)

==============================================================================



AIM:

&#x20; To perform data driven testing through a front-end grid (table) that displays the test data and results.



WHAT WE ARE DOING:

&#x20; 1. Test data (price and category) is stored in a grid-like array.

&#x20; 2. For each row, the discount function is called to compute the result.

&#x20; 3. The rows are added to a Swing JTable with columns Price, Category and Result.

&#x20; 4. The table is shown in a window so the inputs and outputs can be viewed together.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

import javax.swing.\*;

import javax.swing.table.DefaultTableModel;

public class FrontEndGridTest {

&#x20;   public static double calculateDiscount(double price, String category) { switch (category) {

&#x20;           case "electronics": return price \* 0.9; case "clothing": return price \* 0.8; default: return price;

&#x20;       }

&#x20;   }

&#x20;   public static void main(String\[] args) {

&#x20;       JFrame frame = new JFrame("Front End Grid - Data Driven Test");

&#x20;       String\[] columns = {"Price", "Category", "Result"};

&#x20;       DefaultTableModel model = new DefaultTableModel(columns, 0);

&#x20;       Object\[]\[] gridData = {

&#x20;           {500.0, "electronics"},

&#x20;           {300.0, "clothing"},

&#x20;           {150.0, "grocery"}

&#x20;       };

&#x20;       for (Object\[] row : gridData) { double price = (double) row\[0];

&#x20;           String category = (String) row\[1];

&#x20;           double result = calculateDiscount(price, category);

&#x20;           model.addRow(new Object\[]{

&#x20;               price, category, String.format("%.2f", result)});

&#x20;       }

&#x20;       JTable table = new JTable(model);

&#x20;       frame.add(new JScrollPane(table));

&#x20;       frame.setSize(400, 200);

&#x20;       frame.setDefaultCloseOperation(JFrame.EXIT\_ON\_CLOSE);

&#x20;       frame.setVisible(true);

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

Compile / Run Commands

javac FrontEndGridTest.java

java FrontEndGridTest

Output

Price Category Result

500.0 electronics 450.00

300.0 clothing 240.00

150.0 grocery 150.00



\##############################################################################

&#x20;                                  WEEK 10                                    

\##############################################################################



==============================================================================

Experiment 7(e): Batch Testing – Without Parameter Passing (Suite Run)

==============================================================================



AIM:

&#x20; To perform batch testing without parameter passing, running several fixed tests as one suite.



WHAT WE ARE DOING:

&#x20; 1. Two test methods are written: testAddition and testSubtraction.

&#x20; 2. Each method checks a fixed condition using assert and prints PASS.

&#x20; 3. The main method runs all the tests one after another as a batch.

&#x20; 4. No data is passed to the tests; each test has its values written inside it.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

public class BatchNoParams {

&#x20;   public static void testAddition() {

&#x20;       assert 2 + 3 == 5;

&#x20;       System.out.println("test\_addition: PASS");

&#x20;   }

&#x20;   public static void testSubtraction() { assert 5 - 2 == 3;

&#x20;       System.out.println("test\_subtraction: PASS");

&#x20;   }

&#x20;   public static void main(String\[] args) {

&#x20;       System.out.println("---- Batch Testing (No Parameters) ");

&#x20;       testAddition(); testSubtraction();

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

\---- Batch Testing (No Parameters)

test\_addition: PASS

test\_subtraction: PASS



==============================================================================

Experiment 7(f): Batch Testing – With Parameter Passing (Suite Parameters)

==============================================================================



AIM:

&#x20; To perform batch testing with parameter passing, running one test method with many sets of values.



WHAT WE ARE DOING:

&#x20; 1. A single testOperation method accepts two numbers, an operator and the expected result.

&#x20; 2. A list of test cases is stored in an array and passed to the method in a loop.

&#x20; 3. The actual result is compared with the expected one and PASS or FAIL is printed for each case.

&#x20; 4. One deliberately wrong case (5 - 5 expected 1) shows how a FAIL is reported.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

public class BatchWithParams {

&#x20;   static void testOperation(int a, int b, char op, int expected) {

&#x20;       int result = 0;

&#x20;       switch (op) {

&#x20;           case '+': result = a + b;

&#x20;           break;

&#x20;           case '-': result = a - b;

&#x20;           break;

&#x20;           case '\*': result = a \* b;

&#x20;           break;

&#x20;       }

&#x20;       String status = (result == expected) ? "PASS" : "FAIL";

&#x20;       System.out.printf("Test: %d %c %d = %d (expected %d) -> %s%n", a, op, b, result, expected, status);

&#x20;   }

&#x20;   public static void main(String\[] args) {

&#x20;       int\[]\[] testCases = {{2, 3, '+', 5},{10, 4, '-', 6},{3, 3, '\*', 9},{5, 5, '-', 1}};

&#x20;       System.out.println("---- Batch Testing (With Parameters) ");

&#x20;       for (int\[] tc : testCases) {

&#x20;           testOperation(tc\[0], tc\[1], (char) tc\[2], tc\[3]);

&#x20;       }

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

\---- Batch Testing (With Parameters)

Test: 2 + 3 = 5 (expected 5) -> PASS

Test: 10 - 4 = 6 (expected 6) -> PASS

Test: 3 \* 3 = 9 (expected 9) -> PASS

Test: 5 - 5 = 0 (expected 1) -> FAIL



==============================================================================

Experiment 8: Data Driven Batch (Batch + Multiple Data Sets)

==============================================================================



AIM:

&#x20; To perform a data driven batch test, running a batch of tests using multiple data sets from a CSV file.



WHAT WE ARE DOING:

&#x20; 1. A CSV file batch\_data.csv is created with Price, Category and ExpectedResult columns.

&#x20; 2. Each row is read, the discount is calculated and compared with the expected result.

&#x20; 3. PASS or FAIL is printed for every row.

&#x20; 4. A final summary shows the total number of tests passed and failed.



\------------------------------------------------------------------------------

PROGRAM:

\------------------------------------------------------------------------------

import java.io.\*;

public class DataDrivenBatch {

&#x20;   public static double calculateDiscount(double price, String category) {

&#x20;       switch (category) {

&#x20;           case "electronics":

&#x20;           return price \* 0.9;

&#x20;           case "clothing":

&#x20;           return price \* 0.8;

&#x20;           default:

&#x20;           return price;

&#x20;       }

&#x20;   }

&#x20;   public static void createCsvFile() throws IOException {

&#x20;       try (PrintWriter pw = new PrintWriter(new FileWriter("batch\_data.csv"))) {

&#x20;           pw.println("Price,Category,ExpectedResult");

&#x20;           pw.println("500,electronics,450");

&#x20;           pw.println("300,clothing,240");

&#x20;           pw.println("150,grocery,150");

&#x20;           pw.println("1000,electronics,900");

&#x20;       }

&#x20;   }

&#x20;   public static void dataDrivenBatch() throws IOException {

&#x20;       System.out.println("---- Data Driven Batch Test");

&#x20;       int passCount = 0;

&#x20;       int failCount = 0;

&#x20;       try (BufferedReader br = new BufferedReader(new FileReader("batch\_data.csv"))) {

&#x20;           String line = br.readLine();

&#x20;           while ((line = br.readLine()) != null) {

&#x20;               String\[] parts = line.split(",");

&#x20;               double price = Double.parseDouble(parts\[0]);

&#x20;               String category = parts\[1];

&#x20;               double expected = Double.parseDouble(parts\[2]);

&#x20;               double actual = calculateDiscount(price, category);

&#x20;               if (actual == expected) {

&#x20;                   System.out.printf("PASS: %s, price=%.1f -> %.1f%n",

&#x20;                   category, price, actual);

&#x20;                   passCount++;

&#x20;               } else {

&#x20;                   System.out.printf("FAIL: %s, price=%.1f -> got %.1f, expected %.1f%n",

&#x20;                   category, price, actual, expected);

&#x20;                   failCount++;

&#x20;               }

&#x20;           }

&#x20;       }

&#x20;       System.out.println("\\nBatch Summary: " + passCount +

&#x20;       " Passed, " + failCount + " Failed");

&#x20;   }

&#x20;   public static void main(String\[] args) throws IOException {

&#x20;       createCsvFile();

&#x20;       dataDrivenBatch();

&#x20;   }

}



\------------------------------------------------------------------------------

OUTPUT:

\------------------------------------------------------------------------------

\---- Data Driven Batch Test

PASS: electronics, price=500.0 -> 450.0

PASS: clothing, price=300.0 -> 240.0

PASS: grocery, price=150.0 -> 150.0

PASS: electronics, price=1000.0 -> 900.0

Batch Summary: 4 Passed, 0 Failed

