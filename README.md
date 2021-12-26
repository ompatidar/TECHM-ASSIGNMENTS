# Programming Foundation (Practice Assignments) (Ques - Ans)

```
Q1. Write down code or PSEUDO algorithm to find out smallest and largest amongst 3 elements. You can write program in any language you know (C/C++/Java/Python).
```

```java

import java.util.*;

public class FindSM {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
        System.out.println("Input Your 1st, 2nd & 3rd Number: ");
        int num1 = input.nextInt();
        int num2 = input.nextInt();
        int num3 = input.nextInt();

        System.out.println("Choices: "); 
		    System.out.println("1) Smallest number"); 
        System.out.println("2) Largest number");
        
        System.out.printf("Choose Your Option : ");
        int choice = input.nextInt(); 
        input.close();
		    switch(choice) { 
            case 1: 
                int smallest = Math.min(num1, Math.min(num2, num3)); 
                System.out.printf("Smallest Number : %d", smallest); 
                break; 
			      case 2: 
                int largest = Math.max(num1, Math.max(num2, num3));
				        System.out.printf("Largest Number : %d", largest); 
				        break;
		    } 
    }
}
```

```
Q2. Write down code or PSEUDO algorithm to find out roots of a quadratic equation. Please note that roots can be imaginary. You can write program in any language you know (C/C++/Java/Python) OR even you can write PSEUDO Code.
```

```java

import java.util.*;

public class FindQE {

  public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);
    System.out.println("Enter The Values Of a, b & c : ");
    double a = sc.nextDouble();
    double b = sc.nextDouble();
    double c = sc.nextDouble();
    double root1, root2;

    double determinant = b * b - 4 * a * c;

    if (determinant > 0) {

      root1 = (-b + Math.sqrt(determinant)) / (2 * a);
      root2 = (-b - Math.sqrt(determinant)) / (2 * a);
      System.out.println("ANSWER...");
      System.out.format("root1 = %.2f and root2 = %.2f", root1, root2);
    }

    else if (determinant == 0) {

      // two real and equal roots
      // determinant is equal to 0
      // so -b + 0 == -b
      root1 = root2 = -b / (2 * a);
      System.out.println("ANSWER...");
      System.out.format("root1 = root2 = %.2f;", root1);
    }

    else {

      double real = -b / (2 * a);
      double imaginary = Math.sqrt(-determinant) / (2 * a);
      System.out.println("ANSWER...");
      System.out.format("root1 = %.2f+%.2fi", real, imaginary);
      System.out.format("\nroot2 = %.2f-%.2fi", real, imaginary);
    }
  }
}
```

```
Q4. Write PSEUDO algorithm to perform an encryption as well as decryption of a file. Use any algorithm to perform above said activity. Simplest possible algorithm is to read every character, add 128 to it and stores it while performing an encryption and do reverse step while performing a decryption.(You can even give a try to write program in C/C++/Java/Python) 

Your program should a) Read a file character by character b) Encrypt a file d) Display contents of file d) Decrypta file
```

```java

import java.util.*;

public class EncryptDecryptFile {

   static void fileProcessor(int cipherMode,String key,File inputFile,File outputFile){
	 try {
	       Key secretKey = new SecretKeySpec(key.getBytes(), "AES");
	       Cipher cipher = Cipher.getInstance("AES");
	       cipher.init(cipherMode, secretKey);

	       FileInputStream inputStream = new FileInputStream(inputFile);
	       byte[] inputBytes = new byte[(int) inputFile.length()];
	       inputStream.read(inputBytes);

	       byte[] outputBytes = cipher.doFinal(inputBytes);

	       FileOutputStream outputStream = new FileOutputStream(outputFile);
	       outputStream.write(outputBytes);

	       inputStream.close();
	       outputStream.close();

	    } catch (NoSuchPaddingException | NoSuchAlgorithmException 
                     | InvalidKeyException | BadPaddingException
	             | IllegalBlockSizeException | IOException e) {
		e.printStackTrace();
            }
     }
	
     public static void main(String[] args) {
	String key = "SECRET";
	File inputFile = new File("text.txt");
	File encryptedFile = new File("text.encrypted");
	File decryptedFile = new File("decrypted-text.txt");
		
	try {
        EncryptDecryptFile.fileProcessor(Cipher.ENCRYPT_MODE,key,inputFile,encryptedFile);
        EncryptDecryptFile.fileProcessor(Cipher.DECRYPT_MODE,key,encryptedFile,decryptedFile);
	     System.out.println("Success");
	 } catch (Exception ex) {
	     System.out.println(ex.getMessage());
             ex.printStackTrace();
	 }
     }
	
}

Explain: By Kishan [private] (Contact For Explaination.. )
```

```
Q5. Write down an PSEUDO algorithm or code in language you know (C/C++/Java/Python) that reads in a markof a student (which is an integer between 0 and 100) and prints the corresponding grades (A-F).

The mark-to-grade conversion table is as follows:
```

| Grade | A | B | C | D | F |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| Range | >= 80 | 65 - 79 | 50 - 64 | 40 - 49 | < 40 |

#### 1. Modify the program so that it checks if the input is between 0 and 100. If not, it should ask the user to input again until the input is in the correct range. Use while statements.

#### 2. Modify the program so that it repeats the above computation on 50 students. Use while statements.


```java

import java.util.*;

public class Grades {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int number = 0;
        while (true) {
           try {
              System.out.print("Enter Number To Find Grade : ");
              number = sc.nextInt();
              if( number >= 0 && number <= 100){
                if(number >= 80) {
                    System.out.println("Grade 'A'");
                }
                else if(number >= 65 && number <=79) {
                    System.out.println("Grade 'B'");
                }
                else if(number >= 50 && number <=64) {
                    System.out.println("Grade 'C'");
                }
                else if(number >= 40 && number <=49) {
                    System.out.println("Grade 'D'");
                }
                else if(number < 40) {
                    System.out.println("Grade 'F'");
                }
                break;
              }
              System.out.println("Out Of Range... ");
              System.out.println("We Accepts The Range Between 0 - 100 Only ");
   
           } catch (InputMismatchException e) {
              System.out.println("You Didn't Entered An Integer Value.");
              System.out.println("We Accepts an Integer Value Only");
              sc.nextLine();
           }
        }    
    }
}
```
