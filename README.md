﻿using System;

namespace Exercises
{
    class Amicablenumber
    {
        static void Main (string[] args)
    {
        int num1, num2, sum1 = 0, sum2 = 0;
        Console.WriteLine("\n       AMICABLE NUMBERS    \n");
        Console.Write("\n Enter the first number:");
        num1 = Convert.ToInt32(Console.ReadLine());
        Console.Write("\n Enter the second number:");
        num2 = Convert.ToInt32(Console.ReadLine());
        for (int i = 1; i < num1; i++)
        {
            if (num1 % i == 0)
            {
                sum1 += i;
            }
        }
        for (int i = 1; i < num2; i++)
        {
            if (num2 % i == 0)
            {
                sum2 += i;
            }
        }
        if (sum1 == num2 && sum2 == num1)
        {
            Console.WriteLine("\n The numbers {0} and {1} are amiciable.", num1, num2);
        }
        else
        {
            Console.WriteLine("\n The numbers {0} and {1} are not amiciable.", num1, num2);
        }

        }
    }
}
<br>
**output**
![image](https://user-images.githubusercontent.com/98377715/152294101-61e72547-4f6d-42d2-9c3b-0006a3da9530.png)

**  binarytraingle**
using System;

namespace Exercises
{
    class BinaryTraingle
    {
        static void Main(string[] args)
        {
            int number, digit = 1;
            Console.Write("\n Enter the number of lines:");
            number = Convert.ToInt32(Console.ReadLine());
            for (int i = 1; i <= number; i++)
            {
                for (int space = number - i; space > 0; space--)
                {
                    Console.Write(" ");
                }
                for (int j = 0; j < i; j++)
                {
                    Console.Write(digit + " ");
                    digit = (digit == 1) ? 0 : 1;
                }
                Console.Write("\n");
            }

          
        }
    }
}



