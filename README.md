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









