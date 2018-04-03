# checkValidEmail
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace EmailCheck
{
    class Program
    {
        static void Main(string[] args)
        {
            checkEmail();
            Console.ReadKey();

        }
        static void checkEmail()
        {
            Console.WriteLine("Enter an email: ");
            string email = Console.ReadLine();

            #region  No or multiple @
            int count = 0;
            for (int i = 0; i <= email.Length - 1; i++)
            {
                if (email[i] == '@')
                {
                    count++;
                }

            }


            if(count != 1)
            {
                Console.WriteLine("Invalid Email - No or multiple @");
                Console.ReadKey();
                return;
            }

            #endregion

            #region @ found in terminal parts

            if (!(email[0] != '@' && email[email.Length - 1] != '@'))
            {
                Console.WriteLine("Invalid Email - @ found in terminal parts");
                Console.ReadKey();
                return;
            }
            #endregion

            #region Finding the position of @
            int positionOfAt = 0;
            for (int i = 0; i <= email.Length - 1; i++)
            {

                if (email[i] == '@')
                {
                    positionOfAt = i;

                    break;
                }

            }

            //Console.WriteLine("The position of @ is " + positionOfAt);
            #endregion

            #region Do i have at least one . after @.
            count = 0;
            int positionOfDott = 0;
            for (int i = positionOfAt + 1; i <= email.Length - 1; i++)
            {
                if (email[i] == '.')
                {
                    count++;
                    positionOfDott = i;
                }


            }
            if (count == 0)
            {
                Console.WriteLine("inValid email - No . found");
                Console.ReadKey();
                return;
            }


            #endregion

            #region Does . comes immediately after @
            if (email[positionOfAt + 1] == '.')
            {
                Console.WriteLine("InValid email - @ and . are side by side");
                Console.ReadKey();
                return;
            }
            #endregion

            #region Does . come in the end
            if (email[email.Length - 1] == '.')
            {
                Console.WriteLine("Invalid Email - . found at end");
                Console.ReadKey();
                return;
            }
            #endregion

            Console.WriteLine("Valid Email");

        }


    }

}

