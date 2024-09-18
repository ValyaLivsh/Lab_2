# Задание 1 
```
using System;

namespace lab2_1
{
    class Pupil
    {
        protected virtual void Study()
        { Console.WriteLine("Study"); }
        protected virtual void Read()
        { Console.WriteLine("Read"); }
        protected virtual void Write() 
        { Console.WriteLine("Write"); }
        protected virtual void Relax()
        { Console.WriteLine("Relax"); }
        public void Info()
        { this.Study(); this.Read(); this.Write(); this.Relax(); }
    }
    class ExcelentPupil : Pupil
    {
        protected override void Study() { Console.WriteLine("Excelent Study"); }
        protected override void Read() { Console.WriteLine("Read much"); }
        protected override void Write() { Console.WriteLine("Write much"); }
        protected override void Relax() { Console.WriteLine("No relax"); }
    }
    class GoodPupil : Pupil
    {
        protected override void Study() { Console.WriteLine("Good Study"); }
        protected override void Read() { Console.WriteLine("Read a lot"); }
        protected override void Write() { Console.WriteLine("Write a lot"); }
        protected override void Relax() { Console.WriteLine("A little bit relax"); }
    }
    class BadPupil : Pupil
    {
        protected override void Study() { Console.WriteLine("Bad Study"); }
        protected override void Read() { Console.WriteLine("Read nothing"); }
        protected override void Write() { Console.WriteLine("Write nothing"); }
        protected override void Relax() { Console.WriteLine("Relax every day"); }
    }
    class Classroom
    {
        Pupil[] Pupils;
        public Classroom(params Pupil[] pupils)
        {
            int k = pupils.Length;
            Pupils = new Pupil[k];
            for (int i = 0; i < k; i++) { Pupils[i] = pupils[i]; }
        }
        public void ClassBook()
        {
            foreach (Pupil p in Pupils) { p.Info(); }
        }
    }
    class Prog
    {
        static void Main(string[] args)
        {
            GoodPupil masha = new GoodPupil();
            ExcelentPupil vasya = new ExcelentPupil();
            BadPupil petya = new BadPupil();
            GoodPupil dasha = new GoodPupil();
            Classroom A = new Classroom(masha, vasya, petya, dasha);
            A.ClassBook();
        }
    }
}
```
Вывод программы
![image](https://github.com/user-attachments/assets/863c85f1-e20c-4bfa-aa7c-9664193ebd78)
# Задание 2
```
using System;

namespace lab2_2
{
    class Vehicle
    {
        protected int price;
        protected int speed;
        protected int release_year;
        public Vehicle(int price, int speed, int release_year)
        {
            this.price = price;
            this.speed = speed;
            this.release_year = release_year;
        }
        virtual public void Info()
        {
            Console.WriteLine($"{this.price}, {this.speed}, {this.release_year}");
        }
    }
    class Plane : Vehicle
    {
        private int height;
        private int passengers_number;
        public Plane(int height, int passengers_number, int price, int speed, int release_year) : base(price, speed, release_year)
        {
            this.height = height;
            this.passengers_number = passengers_number;
        }
        override public void Info()
        {
            base.Info();
            Console.WriteLine($"{this.height}, {this.passengers_number}");
        }
    }
    class Car : Vehicle
    {
        public Car(int price, int speed, int release_year) : base(price, speed, release_year) { }
    }
    class Ship : Vehicle
    {
        private int passengers_number;
        private string port;
        public Ship(int passengers_number, string port, int price, int speed, int release_year) : base (price, speed, release_year)
        {
            this.passengers_number = passengers_number;
            this.port = port;
        }
        public override void Info()
        {
            base.Info();
            Console.WriteLine($"{this.passengers_number}, {this.port}");
        }
    }
    class Prog
    {
        static void Main(string[] args)
        {
            Plane p = new Plane(100, 250, 10000, 2000, 2005);
            Car c = new Car(1000, 300, 2020);
            Ship s = new Ship(1000, "sochi", 10000000, 80, 1995);
            p.Info();
            c.Info();
            s.Info();
        }
    }
}
```
Вывод программы 
![image](https://github.com/user-attachments/assets/177c38c5-58c5-4bb9-9dec-19d357621278)
# Задание 3
```
using System;

namespace lab2_3
{
    class DocumentWorker
    {
        public virtual void OpenDocument() { Console.WriteLine("Document open"); }
        public virtual void EditDocument() { Console.WriteLine("document editing is available in the PRO version"); }
        public virtual void SaveDocument() { Console.WriteLine("document saving is available in the PRO version"); }
    }
    class ProDocumentWorker : DocumentWorker
    {
        public override void EditDocument() { Console.WriteLine("the document has been edited"); }
        public override void SaveDocument() { Console.WriteLine("The document is saved in the old format, saving in other formats is available in the Expert version"); }
        public override void OpenDocument() { base.OpenDocument(); }
    }
    class ExpertDocumentWorker : ProDocumentWorker
    {
        public override void OpenDocument() { base.OpenDocument(); }
        public override void EditDocument() { base.EditDocument(); }
        public override void SaveDocument() { Console.WriteLine("document has been saved"); }
    }

    class Prog
    {
        static void Main(string[] args)
        {
            string key = Console.ReadLine();
            if (key == " ")
            {
                DocumentWorker document = new DocumentWorker();
                document.OpenDocument();
                document.EditDocument();
                document.SaveDocument();
            }
            if (key == "pro")
            {
                ProDocumentWorker document = new ProDocumentWorker();
                document.OpenDocument();
                document.EditDocument();
                document.SaveDocument();
            }
            if (key == "exp")
            {
                ExpertDocumentWorker document = new ExpertDocumentWorker();
                document.OpenDocument();
                document.EditDocument();
                document.SaveDocument();
            }
        }
    }
}
```
Вывод программы 
![image](https://github.com/user-attachments/assets/a8dcb0b4-2d43-4797-9372-ca4830ca5ecc)
![image](https://github.com/user-attachments/assets/ad1e72f0-2c08-48fe-bec7-7e64dd0e1d58)
![image](https://github.com/user-attachments/assets/1fc3e91e-580e-4336-8bee-302bc0e100b1)


