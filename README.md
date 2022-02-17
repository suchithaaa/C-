using System;

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

<br>
**output**
![image](https://user-images.githubusercontent.com/98377715/152469293-b184bde6-be55-42ae-9c8d-33d29b31b8db.png)


**Graycode**
using System;<br>

namespace Exercises<br>
{<br>
    class GrayCode<br>
    {
        static int getGray(int n)
        {
            return n ^ (n >> 1);
         }
        static void Main(string[] args)
        {
            int InputNum, GrayNum;
            Console.Write("\n Enter the decimal number:");
            InputNum = Convert.ToInt32(Console.ReadLine());
            Console.WriteLine("\n Binary equivalent of {0}: {1}", InputNum, Convert.ToString(InputNum, 2));
            GrayNum = getGray(InputNum);
            Console.WriteLine("\n Graycode equivalent of {0}: {1}", InputNum, Convert.ToString(GrayNum, 2));
        }
    }
}

**volume of 2 boxes**
using System;
namespace Exercises
{
    class Box
    {
        float width;
        float height;
        float length;
        public float volume
        {
            get { return width * height * length; }
        }
        public Box(float width, float height, float length)
        {
            this.width = width;
            this.height = height;
            this.length = length;
        }
        public static float operator +(Box box1, Box box2)
        {
            return box1.volume + box2.volume;
        }
        public override string ToString()
        {
            return "box with width" + width + ",height" + height + " and length" + length;
        }
    }
    class operatoroverloading
    {
        public static void Main()
        {
            Box box1 = new Box(10, 20, 30);
            Box box2 = new Box(25, 32, 15);
            Console.WriteLine("volume of {0} is:{1}", box1, box1.volume);
            Console.WriteLine("volume of {0} is:{1}", box2, box2.volume);
            Console.WriteLine("volume after adding boxes:{0}", box1 + box2);
        }
    }
}
<br>
**  output **
![image](https://user-images.githubusercontent.com/98377715/152473394-73214341-ba4c-4fa1-a10f-a0b1dd4760c2.png)


**   multilevel inheritance**
using System;
namespace Exercises
{
    class personalDetails
    {
        String name;
        int age;
        string gender;
        public personalDetails(string name, int age, string gender)
        {
            this.name = name;
            this.age = age;
            this.gender = gender;
        }
        public virtual void Display()
        {
            Console.WriteLine("\n    PERSONAL DETAILS    \n");
            Console.WriteLine("Name :" + name);
            Console.WriteLine("Age :" + age);
            Console.WriteLine("Gender :" + gender);
        }
    }
    class CourseDetails : personalDetails
    {
        int regNo;
        string course;
        int semester;
        public CourseDetails(string name, int age, string gender, int regNo, string course, int semester) : base(name, age, gender)
        {
            this.regNo = regNo;
            this.course = course;
            this.semester = semester;
        }
        public override void Display()
        {
            base.Display();
            Console.WriteLine("\n    COURSE DETAILS    \n");
            Console.WriteLine("Register Number :" + regNo);
            Console.WriteLine("Course :" + course);
            Console.WriteLine("semester :" + semester);
        }
    }
    class MarksDetails : CourseDetails
    {
        int[] marks = new int[5];
        int total;
        float average;
        string grade;
        int flagFail;
        public MarksDetails(string name, int age, string gender, int regNo, string course, int semester, int[] marks) : base(name, age, gender, regNo, course, semester)
        {
            total = 0;
            for (int i = 0; i < 5; i++)
            {
                this.marks[i] = marks[i];
                total += marks[i];
                if (marks[i] < 35)
                {
                    flagFail = 1;
                }
            }
            Calculate();
        }
        private void Calculate()
        {
            average = total / 5;
            if (flagFail ==1||average<40)
                grade = "Fail";
            else if (average >= 70)
                grade = "Distinction";
            else if (average >= 60)
                grade = "First class";
            else if (average >= 50)
                grade = "second class";
            else
                grade = "pass class";
        }
        public override void Display()
        {
            base.Display();
            Console.WriteLine("\n     MARKS DETAILS   /n");
            Console.Write("Marks in 5 subjects:");
            for (int i = 0; i < 5; i++)
                Console.Write(marks[i] + " ");
            Console.WriteLine();
            Console.WriteLine("Total :" + total);
            Console.WriteLine("Average :" + average);
            Console.WriteLine("Grade :" + grade);
        }
    }
    class Multilevel
    {
        public static void Main(string[] args)
        {
            MarksDetails Student1 = new MarksDetails("Abhijith", 22, "male", 20190001, "MCA", 5, new int[] { 77, 80, 98, 95, 90 });
            Student1.Display();
        }
    }
}
<br>
**   output **
![image](https://user-images.githubusercontent.com/98377715/152480302-f2a1aabb-128c-4f6f-971a-6f6c8f8cc253.png)


**   delegates**
using System;
namespace Exercises
{
    class Delegates
    {
        delegate String UppercaseDelegate(string input);
        static string UppercaseFirst(string input)
        {
            char[] buffer = input.ToCharArray();
            buffer[0] = char.ToUpper(buffer[0]);
            return new string(buffer);
        }
        static string UppercaseLast(string input)
        {
            char[] buffer = input.ToCharArray();
            buffer[buffer.Length - 1] = char.ToUpper(buffer[buffer.Length - 1]);
            return new string(buffer);
        }
        static string UppercaseAll(string input)
        {
            return input.ToUpper();
        }
        static void writeOutput(string input, UppercaseDelegate del)
        {
            Console.WriteLine("Input string:{0}", input);
            Console.WriteLine("Output string:{0}", del(input));
        }
        static void Main()
        {
            writeOutput("tom", new UppercaseDelegate(UppercaseFirst));
            writeOutput("tom", new UppercaseDelegate(UppercaseLast));
            writeOutput("tom", new UppercaseDelegate(UppercaseAll));
            Console.ReadLine();
        }
    }
}
<br>
**  output **
![image](https://user-images.githubusercontent.com/98377715/152482932-045ca89c-138c-49fd-869b-c89862ee8271.png)

**  static constructor **
using System;
namespace Exercises
{
    class RegisterNum
    {
        int regNo;
        static int startNum;
        static RegisterNum()
        {
            startNum = 20210000;
        }
        RegisterNum()
        {
            regNo = ++startNum;
        }
        public static void Main(string[] args)
        {
            for (int i = 0; i < 100; i++)
            {
                RegisterNum Student = new RegisterNum();
                Console.WriteLine("Student {0}:{1}", i + 1, Student.regNo);
            }
        }
    }
}
<br>
** output **
![image](https://user-images.githubusercontent.com/98377715/152485147-c5b8fbcf-968c-4b4c-aced-d2940ca91f19.png)
![image](https://user-images.githubusercontent.com/98377715/152485354-c87db2f5-62f4-407e-8334-2d8b2d0b1723.png)
![image](https://user-images.githubusercontent.com/98377715/152485458-67f3d3eb-8d07-4830-b45d-5c76ba6617c3.png)
![image](https://user-images.githubusercontent.com/98377715/152485527-8fc3f0ba-8399-4043-b026-d89b925b53c7.png)


**  frequency of the word **
using System;
namespace Exercises
{
    class FrequencyIS
    {
        static void Main(string[] args)
        {
            int count = 0;
            String inputString;
            Console.WriteLine("\n     Frequency of word 'is'   ");
            Console.Write("\n Enter the input string :");
            inputString = Console.ReadLine();
            char[] separator = { ',', ' ', '.', '!', '\n' };
            string testString = inputString.ToLower();
            String[] outcomes = testString.Split(separator);
            foreach (String s in outcomes)
            {
                Console.WriteLine(s);
                if (s == "is")
                    count++;
            }
            Console.WriteLine("\n Number of 'is' in"+ inputString +" is:" +count);
                }
    }
}
<br>
**  output **
![image](https://user-images.githubusercontent.com/98377715/152488089-cf8c4480-4b36-42c6-8b4d-05590d13174b.png)


**   jagged array location**
using System;
using System.Diagnostics; 
namespace Exrecises
{
    class BenchmarkAllocation
    {
        const int _max= 100000;
        static void Main(string[] args)
        {
            var Arr2D = new int[100,100];
            var ArrJagged = new int[100][];
            for (int i = 0; i < 100; i++)
            {
                ArrJagged[i] = new int[100];
            }
            var Stopwatch2D = Stopwatch.StartNew();
            for (int i = 0; i < _max; i++)
            {
                for (int j = 0; j < 100; j++)
                {
                    for (int k = 0; k < 100; k++)
                    {
                        Arr2D[j,k] = k;
                    }
                }
            }
            Stopwatch2D.Stop();
            var StopwatchJagged = Stopwatch.StartNew();
            for (int i = 0; i < _max; i++)
            {
                for (int j = 0; j < 100; j++)
                {
                    for (int k = 0; k < 100; k++)
                    {
                        ArrJagged[j][k] = k;
                    }
                }
            }
            StopwatchJagged.Stop();
            Console.Write("\n Time taken for allocation in case of 2D array:");
            Console.WriteLine(Stopwatch2D.Elapsed.TotalMilliseconds + "millisecods");
            Console.Write("\n Time taken for allocation in case of Jagged array:");
            Console.WriteLine(StopwatchJagged.Elapsed.TotalMilliseconds + "milliseconds");
        }
    }
}
<br>
**   output**
![image](https://user-images.githubusercontent.com/98377715/154411159-282f0942-ce13-49aa-b475-7404b116729a.png)



**   diagonal matrix**

using System;
namespace Exercises
{
    class SumOfDiagonals
    {
        static void Main(string[] args)
        {
            int MaxRow, Maxcol, Sum = 0;
            int[,] Matrix;
            Console.WriteLine("\n -----SUM OF DIAGONAL OF A MATRIX ----\n");
            Console.Write("\n Enter the number of rows:");
            MaxRow = Convert.ToInt32(Console.ReadLine());
            Console.Write("\n Enter the number of columns:");
            Maxcol = Convert.ToInt32(Console.ReadLine());
            if (MaxRow != Maxcol)
            {
                Console.WriteLine("\n The Dimensions entered are not of Square Matrix.");
                Console.WriteLine("\n Exiting the program.");
                return;
            }
            Matrix = new int[MaxRow, Maxcol];
            for (int i = 0; i < MaxRow; i++)
            {
                for (int j = 0; j < Maxcol; j++)
                {
                    Console.Write("\n Enter the ({0},{1})th element of the matrix:", (i + 1), (j + 1));
                    Matrix[i, j] = Convert.ToInt32(Console.ReadLine());
                }
            }
            Console.WriteLine("\n The entered Matrix is:");
            for (int i = 0; i < MaxRow; i++)
            {
                for (int j = 0; j < Maxcol; j++)
                {
                    Console.Write(" " + Matrix[i, j]);
                    if (i == j)
                    {
                        Sum += Matrix[i, j];
                    }
                }
                Console.WriteLine();
            }
            Console.WriteLine("\n The Sum of Diagonal is" + Sum);
        }
    }
}
<br>
**  output  **
![image](https://user-images.githubusercontent.com/98377715/154416175-8e73abc5-9c0f-4db3-baf6-8ed4f44ba9e8.png)
![image](https://user-images.githubusercontent.com/98377715/154416251-6b19654c-56e2-4126-8c78-01a5ab6f9b33.png)













