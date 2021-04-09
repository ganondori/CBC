using System;

namespace Char_by_char
{
    class program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            int edad;
            string Nombre, Apellido, C1, C2;
            double ahorros;

            System.Console.WriteLine("Cual es su nombre?");
            Nombre = JL();
            System.Console.WriteLine("Cual es su apellido?");
            Apellido = JL();
            System.Console.WriteLine("Diga su edad");
            edad = JN();
            while(true)
            {
                System.Console.WriteLine("Digite la clave");
                C1 = CL();
                System.Console.WriteLine("Confirme la clave");
                C2 = CL();
                if(C1 == C2)
                {
                    break;
                }
                else
                {
                    Console.Clear();
                    System.Console.WriteLine("Las claves no coinciden");
                    System.Console.WriteLine("\n");
                }
            }
            System.Console.WriteLine("Diga sus ahorros");
            ahorros = AH();

            System.Console.WriteLine("Estos son sus datos:");
            System.Console.WriteLine("*********************************************************************");
            System.Console.WriteLine("\n");
            System.Console.WriteLine(Nombre);
            System.Console.WriteLine(Apellido);
            System.Console.WriteLine(edad);
            System.Console.WriteLine(ahorros);
            System.Console.WriteLine(C1 + " Primera clave");
            System.Console.WriteLine(C2 + " Segunda clave");
            System.Console.WriteLine("\n");
            System.Console.WriteLine("*********************************************************************");

        }
        static int JN()
        {
            ConsoleKey k;
            string data = "";
            do
            {
                var inf = Console.ReadKey(true);
                k = inf.Key;
                int val;
                bool ex = int.TryParse(inf.KeyChar.ToString(), out val);

                if(k == ConsoleKey.Backspace && data.Length > 0)
                {
                    Console.Write("\b \b");
                    data = data.Remove(data.Length - 1);
                }
                else if(!Char.IsControl(inf.KeyChar) && ex)
                {
                    Console.Write(inf.KeyChar);
                    data += inf.KeyChar;
                }
            }while(k != ConsoleKey.Enter);
            System.Console.WriteLine("\n");
            return Convert.ToInt32(data);
        }

        static string JL()
        {
            ConsoleKey k;
            string data = "";
            do
            {
                var inf = Console.ReadKey(true);
                k = inf.Key;

                if(k == ConsoleKey.Backspace && data.Length > 0)
                {
                    Console.Write("\b \b");
                    data = data.Remove(data.Length - 1);
                }
                else if(!Char.IsControl(inf.KeyChar) && !Char.IsNumber(inf.KeyChar))
                {
                    Console.Write(inf.KeyChar);
                    data += inf.KeyChar;
                }
            }while(k != ConsoleKey.Enter);
            System.Console.WriteLine("\n");
            return data;
        }

        static double AH()
        {
            ConsoleKey k;
            string data = "";
            int counter = 0;
            do
            {
                var inf = Console.ReadKey(true);
                k = inf.Key;
                int val;
                bool ex = int.TryParse(inf.KeyChar.ToString(), out val);

                if(k == ConsoleKey.Backspace && data.Length > 0)
                {
                    Console.Write("\b \b");
                    data = data.Remove(data.Length - 1);
                }
                else if(!Char.IsControl(inf.KeyChar) && ex && counter < 3 || Char.IsPunctuation(inf.KeyChar))
                {
                    if(counter >= 1)
                    {
                        counter++;
                    }
                    
                    Console.Write(inf.KeyChar);
                    data += inf.KeyChar;
                    

                    if(Char.IsPunctuation(inf.KeyChar))
                    {
                        counter++;
                    }
                    
                }
            }while(k != ConsoleKey.Enter);
            System.Console.WriteLine("\n");
            return Convert.ToDouble(data);
        }
        static string CL()
        {
            ConsoleKey k;
            string data = "";
            do
            {
                var inf = Console.ReadKey(true);
                k = inf.Key;

                if(k == ConsoleKey.Backspace && data.Length > 0)
                {
                    Console.Write("\b \b");
                    data = data.Remove(data.Length - 1);
                }
                else if(!Char.IsControl(inf.KeyChar))
                {
                    Console.Write("*");
                    data += inf.KeyChar;
                }
            }while(k != ConsoleKey.Enter);
            System.Console.WriteLine("\n");
            return data;
        }
    }
}
