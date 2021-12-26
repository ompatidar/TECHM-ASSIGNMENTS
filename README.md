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
