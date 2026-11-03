\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*





**Experiment 2: GUI Checkpoint for Single Property (Title/Text/Attribute)**



import javax.swing.JFrame;

&#x20;public class program {

&#x20;public static void main(String\[] args) throws InterruptedException {

JFrame frame = new JFrame("Google");

frame.setSize(400, 200);

frame.setDefaultCloseOperation(JFrame.EXIT\_ON\_CLOSE);

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

&#x20;}



**output :**

**Actual Title : Google**

**Expected Title : Google**

**PASS: Title is correct**





\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*







**Experiment 3: GUI Checkpoint for Single Object/Window (Displayed/Enabled)**





import javax.swing.\*;

public class program {

public static void main(String\[] args) throws InterruptedException

&#x20;{

&#x20;JFrame frame = new JFrame("Single Object Checkpoint");

&#x20;JTextField searchBox = new JTextField(20);

&#x20;JPanel panel = new JPanel();

&#x20;panel.add(new JLabel("Search:"));

&#x20;panel.add(searchBox);

&#x20;frame.add(panel);

&#x20;frame.setSize(400, 150);

&#x20;frame.setDefaultCloseOperation(JFrame.EXIT\_ON\_CLOSE);

&#x20;frame.setLocationRelativeTo(null);

&#x20;frame.setVisible(true);

&#x20;Thread.sleep(500);

&#x20;boolean displayed = searchBox.isShowing();

&#x20;boolean enabled= searchBox.isEnabled();

&#x20;System.out.println("Displayed: " + displayed);

&#x20;System.out.println("Enabled : " + enabled);



&#x20;System.out.println(displayed \&\& enabled

? "PASS: Search box is ready"

: "FAIL: Search box is not ready");

&#x20;Thread.sleep(2000); frame.dispose();

&#x20;}

&#x20;}



**output:**



**Displayed: true**

**Enabled : true**

**PASS: Search box is ready**









\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*











**Experiment 4(a): Bitmap Checkpoint for Object/Window (Screenshot Comparison)** 





import javax.swing.\*;

import javax.imageio.ImageIO;

import java.awt.\*;

import java.awt.image.BufferedImage; import java.io.File;

public class NewTest {

public static void main(String\[] args) throws Exception {

JFrame frame = new JFrame("Bitmap Checkpoint Test");

JTextField searchBox = new JTextField("Search here", 20);

JPanel panel = new JPanel();

panel.add(searchBox);

frame.add(panel);

frame.setSize(350, 120);

frame.setDefaultCloseOperation(JFrame.EXIT\_ON\_CLOSE);

frame.setLocationRelativeTo(null); frame.setVisible(true);

Thread.sleep(1000);

File folder = new File("Screenshots");

if (!folder.exists()) folder.mkdir();

BufferedImage currentImage = new BufferedImage( searchBox.getWidth(), searchBox.getHeight(),

BufferedImage.TYPE\_INT\_RGB);

Graphics2D g2 = currentImage.createGraphics();

searchBox.paint(g2);

g2.dispose();

File currentFile = new File("Screenshots/current\_searchbox.png");

ImageIO.write(currentImage, "png", currentFile);

System.out.println("Current screenshot saved:");

System.out.println(currentFile.getAbsolutePath());

File baselineFile = new File("Screenshots/baseline\_searchbox.png");

if (!baselineFile.exists()) {

System.out.println("Baseline image not found.");

System.out.println("Rename current\_searchbox.png as baseline\_searchbox.png");

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







**OUTPUT:**



**Current screenshot saved:**

**C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm\\Screenshots\\current\_searchbox.png**

**BITMAP CHECKPOINT : TEST PASS**

**Images are identical.**







\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*





**Experiment 4(b): Bitmap Checkpoint for Screen Area (Crop + Compare)**





import javax.swing.\*;

import javax.imageio.ImageIO;

import java.awt.\*;

import java.awt.image.BufferedImage;

import java.io.File;

public class NewTest {

&#x20;public static void main(String\[] args) throws Exception {

&#x20;JFrame frame = new JFrame("Bitmap Area Checkpoint");

&#x20;JPanel panel = new JPanel(new FlowLayout());

&#x20;panel.add(new JLabel("Google Search"));

&#x20;panel.add(new JTextField(25));

panel.add(new JButton("Search"));

frame.add(panel);

frame.setSize(800, 600);

frame.setDefaultCloseOperation(JFrame.EXIT\_ON\_CLOSE);

frame.setLocationRelativeTo(null);

frame.setVisible(true);

Thread.sleep(1000);

BufferedImage fullImage = new BufferedImage(frame.getWidth(), frame.getHeight(),

BufferedImage.TYPE\_INT\_RGB);

Graphics2D g2 = fullImage.createGraphics();

frame.paint(g2);

g2.dispose();

File folder = new File("SeleniumScreenshots");

if (!folder.exists())

&#x20;folder.mkdirs();

int width = Math.min(800, fullImage.getWidth());

int height = Math.min(600, fullImage.getHeight());

BufferedImage currentArea = fullImage.getSubimage(0, 0, width, height);

File currentFile = new File("SeleniumScreenshots/current\_google\_area.png");

ImageIO.write(currentArea, "png", currentFile);

System.out.println("Current screenshot saved:");

System.out.println(currentFile.getAbsolutePath());

File baselineFile = new File("SeleniumScreenshots/baseline\_google\_area.png");

if (!baselineFile.exists()) {

System.out.println("Baseline image not found.");

System.out.println("Rename current\_google\_area.png to baseline\_google\_area.png");

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

&#x20;public static double compareImages(BufferedImage img1, BufferedImage img2) {

&#x20;if (img1.getWidth() != img2.getWidth() ||

img1.getHeight() != img2.getHeight()) return 0;

long totalPixels = (long) img1.getWidth() \* img1.getHeight();

long samePixels = 0;

for (int x = 0; x < img1.getWidth(); x++) {

for (int y = 0; y < img1.getHeight(); y++) {

if (img1.getRGB(x, y) == img2.getRGB(x, y)) samePixels++;

}

}

return ((double) samePixels / totalPixels) \* 100;

}

}









**OUTPUT:**

**Current screenshot saved:**

**C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm\\SeleniumScreenshots\\current\_google\_area.png**

**Image Similarity : 100.00%**

**BITMAP CHECKPOINT : TEST PASS**







\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*







**Experiment 5: Database Checkpoint – Default Check (Record Exists)**





**import java.sql.Connection;**

**import java.sql.DriverManager;**

**import java.sql.ResultSet;**

**import java.sql.Statement;**

**public class NewTest {**

**public static void main(String\[] args) {**

**try {**

**Connection con = DriverManager.getConnection( "jdbc:h2:./StudentDB", "sa", "");**

**Statement stmt = con.createStatement();**

**stmt.execute("CREATE TABLE IF NOT EXISTS STUDENT (" + "ID INT PRIMARY KEY, " +**

**"NAME VARCHAR(50), " + "EMAIL VARCHAR(100))");**

**stmt.execute("DELETE FROM STUDENT");**

**stmt.executeUpdate("INSERT INTO STUDENT VALUES " +**

**"(1, 'Ajay', 'ajay@gmail.com')");**

**ResultSet rs = stmt.executeQuery(**

**"SELECT \* FROM STUDENT WHERE ID = 1");**

**if (rs.next()) {**

**System.out.println("Record Exists");**

&#x20;**System.out.println("ID : " + rs.getInt("ID"));**

&#x20;**System.out.println("Name : " + rs.getString("NAME"));**

&#x20;**System.out.println("Email : " + rs.getString("EMAIL"));**

&#x20;**System.out.println("TEST PASSED");**

&#x20;**} else {**

**System.out.println("Record Not Found");**

**System.out.println("TEST FAILED");**

**}**

**rs.close();**

**stmt.close();**

**con.close();**

**} catch (Exception e) {**

**e.printStackTrace();**

**}**

**}**

**}**

&#x20;**OUTPUT:**



**PS C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm> javac -cp ".;lib\\h2-2.5.252.jar" NewTest.java**

**PS C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm> java -cp ".;lib\\h2-2.5.252.jar" NewTest**

**Record Exists**

**ID : 1**

**Name : Ajay**

**Email : ajay@gmail.com**

**TEST PASSED**





\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*











**Experiment 6: Database Checkpoint – Custom Check (Validate Specific Value)**



**import java.sql.\*;**

**public class DatabaseCheckpointCustomCheck {**

&#x20;   **static final String DB\_URL = "jdbc:h2:./student";**

&#x20;   **public static void setupDatabase() throws SQLException {**

&#x20;       **try (Connection conn = DriverManager.getConnection(DB\_URL);**

&#x20;            **Statement stmt = conn.createStatement()) {**

&#x20;           **stmt.execute("CREATE TABLE IF NOT EXISTS students (" +**

&#x20;                   **"id INTEGER PRIMARY KEY, name VARCHAR(50), marks INTEGER)");**

&#x20;           **stmt.execute("DELETE FROM students");**

&#x20;           **stmt.execute("INSERT INTO students VALUES (1, 'Amit', 78)");**

&#x20;           **stmt.execute("INSERT INTO students VALUES (2, 'Neha', 45)");**

&#x20;           **stmt.execute("INSERT INTO students VALUES (3, 'Ravi', 92)");**

&#x20;       **}**

&#x20;   **}**

&#x20;   **public static boolean customCheckpoint(int studentId, String expectedStatus)**

&#x20;           **throws SQLException {**

&#x20;       **try (Connection conn = DriverManager.getConnection(DB\_URL);**

&#x20;            **PreparedStatement ps = conn.prepareStatement(**

&#x20;                    **"SELECT marks FROM students WHERE id = ?")) {**

&#x20;           **ps.setInt(1, studentId);**

&#x20;           **ResultSet rs = ps.executeQuery();**

&#x20;           **if (!rs.next()) {**

&#x20;               **System.out.println("FAIL: No record found for id " + studentId);**

&#x20;               **return false;**

&#x20;           **}**

&#x20;           **int marks = rs.getInt("marks");**

&#x20;           **String actualStatus = (marks >= 50) ? "Pass" : "Fail";**

&#x20;           **if (actualStatus.equals(expectedStatus)) {**

&#x20;               **System.out.println("PASS: Student " + studentId +**

&#x20;                       **" status = " + actualStatus +**

&#x20;                       **" (Custom check matched)");**

&#x20;               **return true;**

&#x20;           **} else {**

&#x20;               **System.out.println("FAIL: Student " + studentId +**

&#x20;                       **" expected " + expectedStatus +**

&#x20;                       **", got " + actualStatus);**

&#x20;               **return false;**

&#x20;           **}**

&#x20;       **}**

&#x20;   **}**

&#x20;   **public static void main(String\[] args) throws Exception {**

&#x20;       **setupDatabase();**

&#x20;       **customCheckpoint(1, "Pass");**

&#x20;       **customCheckpoint(2, "Fail");**

&#x20;       **customCheckpoint(3, "Pass");**

&#x20;   **}**

**}**



&#x20;

**OUTPUT:**





**PS C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm> javac -cp ".;lib\\h2-2.5.252.jar" DatabaseCheckpointCustomCheck.java**

**PS C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm> java -cp ".;lib\\h2-2.5.252.jar" DatabaseCheckpointCustomCheck**

**PASS: Student 1 status = Pass (Custom check matched)**

**PASS: Student 2 status = Fail (Custom check matched)**

**PASS: Student 3 status = Pass (Custom check matched)**







\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*







**Experiment 7(a): Data Driven Test – Dynamic Test Data Submission**







**import java.util.Random;**

**public class DynamicDataTest {**

**public static double calculateDiscount(double price, String category) { switch (category) {**

**case "electronics": return price \* 0.9; case "clothing": return price \* 0.8; default: return price;**

**}**

**}**

**public static void main(String\[] args) {**

**String\[] categories = {"electronics", "clothing", "grocery"}; Random rand = new Random();**

**System.out.println("---- Dynamic Test Data Submission ");**

**for (int i = 1; i <= 5; i++) {**

**int price = 100 + rand.nextInt(901);**

**String category = categories\[rand.nextInt(categories.length)];**

**double result = calculateDiscount(price, category);**

**System.out.printf(**

**"Test %d: price=%d, category=%s -> discounted=%.2f%n", i, price, category, result);**

**}**

**}**

**}**







**OUTPUT:**

**---- Dynamic Test Data Submission** 

**Test 1: price=755, category=grocery -> discounted=755.00**

**Test 2: price=784, category=clothing -> discounted=627.20**

**Test 3: price=591, category=electronics -> discounted=531.90**

**Test 4: price=419, category=electronics -> discounted=377.10**

**Test 5: price=277, category=clothing -> discounted=221.60**

**PS C:\\Users\\DELL\\Desktop\\dsa\_in\_java\\stm>** 











\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*







**Experiment 7(b): Data Driven Test – Through Flat Files (CSV/TXT)**





**import java.io.\*;**

**public class FlatFileTest {**

**public static double calculateDiscount(double price, String category) { switch (category) {**

**case "electronics": return price \* 0.9; case "clothing": return price \* 0.8; default: return price;**

**}**

**}**

**public static void createFlatFile() throws IOException {**

**try (PrintWriter pw = new PrintWriter(new FileWriter("testdata.txt")))**

**{**

**pw.println("500,electronics");**

**pw.println("300,clothing"); pw.println("150,grocery");**

**}**

**}**

**public static void flatFileTest() throws IOException {**

**System.out.println("---- Data Driven Test via Flat File ");**

**try (BufferedReader br = new BufferedReader( new FileReader("testdata.txt")))**

**{**

**String line;**

**while ((line = br.readLine()) != null) { String\[] parts = line.split(",");**

**double price = Double.parseDouble(parts\[0]); String category = parts\[1];**

**double result = calculateDiscount(price, category);**

**System.out.printf(**

&#x20;**"price=%.1f, category=%s -> discounted=%.2f%n", price, category, result);**

**}**

**}**

**}**

**public static void main(String\[] args) throws IOException { createFlatFile();**

**flatFileTest();**

**}**

**}**





**Compile / Run Commands**

**javac FlatFileTest.java**

**java FlatFileTest**

**Output**

**---- Data Driven Test via Flat File ----**

**price=500.0, category=electronics -> discounted=450.00**

**price=300.0, category=clothing -> discounted=240.00**

**price=150.0, category=grocery -> discounted=150.0**







\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*













&#x20;**Experiment 7(c): Data Driven Test – Through Front Grids (Web Tables)**



**import javax.swing.\*;**

**import javax.swing.table.DefaultTableModel;**

**public class FrontEndGridTest {**

**public static double calculateDiscount(double price, String category) { switch (category) {**

**case "electronics": return price \* 0.9; case "clothing": return price \* 0.8; default: return price;**

**}**

**}**

**public static void main(String\[] args) {**

**JFrame frame = new JFrame("Front End Grid - Data Driven Test");**

**String\[] columns = {"Price", "Category", "Result"};**

**DefaultTableModel model = new DefaultTableModel(columns, 0);**

**Object\[]\[] gridData = {**

**{500.0, "electronics"},**

**{300.0, "clothing"},**

**{150.0, "grocery"}**

**};**

**for (Object\[] row : gridData) { double price = (double) row\[0];**

**String category = (String) row\[1];**

**double result = calculateDiscount(price, category);**

**model.addRow(new Object\[]{**

**price, category, String.format("%.2f", result)});**

**}**

**JTable table = new JTable(model);**

**frame.add(new JScrollPane(table));**

**frame.setSize(400, 200);**

**frame.setDefaultCloseOperation(JFrame.EXIT\_ON\_CLOSE);**

**frame.setVisible(true);**

**}**

**}**





**Compile / Run Commands**

**javac FrontEndGridTest.java**

**java FrontEndGridTest**

**Output**

**Price Category Result**

**500.0 electronics 450.00**

**300.0 clothing 240.00**

**150.0 grocery 150.00**













**Compile / Run Commands**

**javac FrontEndGridTest.java**

**java FrontEndGridTest**

**Output**

**Price Category Result**

**500.0 electronics 450.00**

**300.0 clothing 240.00**

**150.0 grocery 150.00**









\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*











**Week10**



**Experiment 7(e): Batch Testing – Without Parameter Passing (Suite Run)**





&#x20;**public class BatchNoParams {**

&#x20;**public static void testAddition() {**

&#x20;**assert 2 + 3 == 5;**

&#x20;**System.out.println("test\_addition: PASS");**

&#x20;**}**

&#x20;**public static void testSubtraction() { assert 5 - 2 == 3;**

&#x20;**System.out.println("test\_subtraction: PASS");**

&#x20;**}**

&#x20;**public static void main(String\[] args) {**

&#x20;**System.out.println("---- Batch Testing (No Parameters) ");**

&#x20;**testAddition(); testSubtraction();**

&#x20;**}**

&#x20;**}**





**OUTPUT:**



**---- Batch Testing (No Parameters)** 

**test\_addition: PASS**

**test\_subtraction: PASS**







\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*







**Experiment 7(f): Batch Testing – With Parameter Passing (Suite Parameters)**





**public class BatchWithParams {**

**static void testOperation(int a, int b, char op, int expected) {**

**int result = 0;**

**switch (op) {**

**case '+': result = a + b;**

&#x20;**break;**

&#x20;**case '-': result = a - b;**

&#x20;**break;**

&#x20;**case '\*': result = a \* b;**

&#x20;**break;**

&#x20;**}**

&#x20;**String status = (result == expected) ? "PASS" : "FAIL";**

&#x20;**System.out.printf("Test: %d %c %d = %d (expected %d) -> %s%n", a, op, b, result, expected, status);**

&#x20;**}**

&#x20;**public static void main(String\[] args) {**

&#x20;**int\[]\[] testCases = {{2, 3, '+', 5},{10, 4, '-', 6},{3, 3, '\*', 9},{5, 5, '-', 1}};**

&#x20;**System.out.println("---- Batch Testing (With Parameters) ");**

&#x20;**for (int\[] tc : testCases) {**

&#x20;**testOperation(tc\[0], tc\[1], (char) tc\[2], tc\[3]);**

&#x20;**}**

&#x20;**}**

&#x20;**}**





**OUTPUT:**

**---- Batch Testing (With Parameters)**

**Test: 2 + 3 = 5 (expected 5) -> PASS**

**Test: 10 - 4 = 6 (expected 6) -> PASS**

**Test: 3 \* 3 = 9 (expected 9) -> PASS**

**Test: 5 - 5 = 0 (expected 1) -> FAIL**









\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*









**Experiment 8: Data Driven Batch (Batch + Multiple Data Sets)**





**import java.io.\*;**



**public class DataDrivenBatch {**





**public static double calculateDiscount(double price, String category) {**



&#x20;   **switch (category) {**

&#x20;       **case "electronics":**

&#x20;           **return price \* 0.9;**



&#x20;       **case "clothing":**

&#x20;           **return price \* 0.8;**



&#x20;       **default:**

&#x20;           **return price;**

&#x20;   **}**

**}**



**public static void createCsvFile() throws IOException {**



&#x20;   **try (PrintWriter pw = new PrintWriter(new FileWriter("batch\_data.csv"))) {**



&#x20;       **pw.println("Price,Category,ExpectedResult");**

&#x20;       **pw.println("500,electronics,450");**

&#x20;       **pw.println("300,clothing,240");**

&#x20;       **pw.println("150,grocery,150");**

&#x20;       **pw.println("1000,electronics,900");**

&#x20;   **}**

**}**



**public static void dataDrivenBatch() throws IOException {**



&#x20;   **System.out.println("---- Data Driven Batch Test");**



&#x20;   **int passCount = 0;**

&#x20;   **int failCount = 0;**



&#x20;   **try (BufferedReader br = new BufferedReader(new FileReader("batch\_data.csv"))) {**



&#x20;       **String line = br.readLine();**



&#x20;       **while ((line = br.readLine()) != null) {**



&#x20;           **String\[] parts = line.split(",");**



&#x20;           **double price = Double.parseDouble(parts\[0]);**

&#x20;           **String category = parts\[1];**

&#x20;           **double expected = Double.parseDouble(parts\[2]);**



&#x20;           **double actual = calculateDiscount(price, category);**



&#x20;           **if (actual == expected) {**



&#x20;               **System.out.printf("PASS: %s, price=%.1f -> %.1f%n",**

&#x20;                       **category, price, actual);**



&#x20;               **passCount++;**



&#x20;           **} else {**



&#x20;               **System.out.printf("FAIL: %s, price=%.1f -> got %.1f, expected %.1f%n",**

&#x20;                       **category, price, actual, expected);**



&#x20;               **failCount++;**

&#x20;           **}**

&#x20;       **}**

&#x20;   **}**



&#x20;   **System.out.println("\\nBatch Summary: " + passCount +**

&#x20;           **" Passed, " + failCount + " Failed");**

**}**



**public static void main(String\[] args) throws IOException {**



&#x20;   **createCsvFile();**



&#x20;   **dataDrivenBatch();**

**}**





**}**

&#x20;   





**OUTPUT:**



**---- Data Driven Batch Test**

**PASS: electronics, price=500.0 -> 450.0**

**PASS: clothing, price=300.0 -> 240.0**

**PASS: grocery, price=150.0 -> 150.0**

**PASS: electronics, price=1000.0 -> 900.0**



**Batch Summary: 4 Passed, 0 Failed**

































