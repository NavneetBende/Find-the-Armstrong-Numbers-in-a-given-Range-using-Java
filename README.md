# Find-the-Armstrong-Numbers-in-a-given-Range-using-Java

Find the Armstrong Numbers in a given Range using Java
Given two integer inputs as high and low, the objective is to find all the Armstrong Numbers that falls under the limits [Low,High] interval. Before Going into the Explanation let’s understand the problem and the definition of Armstrong Numbers.

Armstrong Number
In number theory, an Armstrong number or a Narcissistic number in a given number base b is a number that is the sum of its own digits each raised to the power of the number of digits.
A number is an Armstrong Number if and only if it can be represented in the following form,

abcd...nth = pow(a,n) + pow(b,n) + pow(c,n) + pow(d,n) + .... pow(nth,n)
Here are some example to understand the definition

Example 1
Input : 120
Output : No
120 is not a Armstrong number.
1*1*1 + 2*2*2 + 0*0*0 = 9

Example 2
Input : 1253
Output : No
1253 is not a Armstrong Number
1*1*1*1 + 2*2*2*2 + 5*5*5*5 + 3*3*3*3 = 723
From the above explanation we gather that to check if a number is it must be represented in the above stated equation. We then check

Find the Armstrong Numbers in a given Range using Java
While loop in C
Java Code
Method 1
This is a simple iterative method to find all Armstrong numbers between two ranges –
Run
//Java program to print armstrong numbers between two intervals
import java.util.Scanner;

public class LearnCoding2
{
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter lower and upper ranges : ");
        int low = sc.nextInt();
        int high = sc.nextInt();

        System.out.println("Armstrong numbers between "+ low + " and " + high + " are : ");

        // loop for finding and printing all armstrong numbers between given range
        for(int num = low ; num <= high ; num++)
        {
            int sum = 0, temp, digit, len;

            len = getOrder(num);
            temp = num;
            // loop to extract digit, find ordered power of digits & add to sum
            while(temp != 0)
            {
                // extract digit
                digit = temp % 10;

                // add power to sum
                sum = sum + (int) Math.pow(digit,len);
                temp /= 10;
            };

            if(sum == num)
                System.out.print(num + " ");
        }

    }

    private static int getOrder(int num) {
            int len = 0;
            while (num!=0)
            {
                len++;
                num = num/10;
            }
            return len;
    }
}
Output
Enter lower and upper ranges : 1 1000
Armstrong numbers between 1 and 1000 are : 
1 2 3 4 5 6 7 8 9 153 370 371 407 
Working
Working of the above code is given below –

Ask the user to enter two ranges, one starting range and the second ending range.
Use a loop to find all Armstrong numbers between starting range and ending range.
Use the logic for checking number is Armstrong or not for every number between the given range and then display the result.
Method 2 (Recursive)
This method uses a recursive approach to find Armstrong sum. You can check recursion in Java here
Run
import java.util.Scanner;

public class LearnCoding2
{
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter lower and upper ranges : ");
        int low = sc.nextInt();
        int high = sc.nextInt();

        System.out.println("Armstrong numbers between "+ low + " and " + high + " are : ");

        // loop for finding and printing all armstrong numbers between given range
        for(int num = low ; num <= high ; num++)
        {
            int len = getOrder(num);

            if(num == getArmstrongSum(num, len))
                System.out.print(num + " ");
        }

    }

    private static int getOrder(int num) {
            int len = 0;
            while (num!=0)
            {
                len++;
                num = num/10;
            }
            return len;
    }
    private static int getArmstrongSum(int num, int order) {
        if(num == 0)
            return 0;

        int digit = num % 10;

        return (int) Math.pow(digit, order) + getArmstrongSum(num/10, order);
    }
}
Output
Enter lower and upper ranges : 1 1000
Armstrong numbers between 1 and 1000 are : 
1 2 3 4 5 6 7 8 9 153 370 371 407
