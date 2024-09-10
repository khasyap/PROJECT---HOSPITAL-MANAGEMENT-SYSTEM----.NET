using System;
using System.Collections.Generic;
using System.Threading;
using System.Xml.Linq;
class project1
{
    public static void Main(string[] args)
    {
        
        List<string> dname = new List<string>();
        List<string> dsp = new List<string>();
        List<string> dadd = new List<string>();
        List<string> dg = new List<string>();
        List<int> dage = new List<int>();
        List<long> dph = new List<long>();
        List<string> did = new List<string>();

        List<string> rname = new List<string>();
        List<string> radd = new List<string>();
        List<string> rg = new List<string>();
        List<int> rage = new List<int>();
        List<long> rph = new List<long>();
        List<string> rid = new List<string>();

        List<string> pname = new List<string>();
        List<string> padd = new List<string>();
        List<string> pdis = new List<string>();
        List<string> pg = new List<string>();
        List<int> page = new List<int>();
        List<long> pph = new List<long>();
        List<long> pid = new List<long>();
        List<string> med = new List<string>();
        List<int> qu = new List<int>();
        qu.Add(89); qu.Add(129);
        qu.Add(98); qu.Add(50);
        qu.Add(49); qu.Add(45);
        string doc="", pat, uid;
        long uid1;
        Console.Clear();
    x:
        Console.ForegroundColor = ConsoleColor.Cyan;
        Console.WriteLine("\t\t\t\t\t\tHOSPITAL MANAGEMENT SYSTEM");
        Console.WriteLine();
        Console.WriteLine();
        Console.WriteLine("═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════");
        Console.WriteLine();
        Console.WriteLine();
        Console.WriteLine("\t\t\t\t\t\tWelcome to login portal");
        Console.WriteLine();
        Console.WriteLine();
        Console.Write("\n1.Doctor Registration and login portal\n\n2.Reception Registration and login portal\n\n3.Patient Registration and login portal\n\n4.Exit\n\nEnter your Choice : ");
        int n = Convert.ToInt32(Console.ReadLine());
        Console.WriteLine("\n\n");
        int ch;
        while (n <= 4 && n > 0)
        {
            if (n == 1)
            {
                Thread.Sleep(1000);            
                Console.Clear();   
            j:
                Console.ForegroundColor = ConsoleColor.Blue;
                Console.WriteLine();
                Console.WriteLine("\n\t\t\t\t\tWelcome to registration portal for Doctors");
                Console.WriteLine();
                Console.WriteLine("═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════\n");
                Console.Write("\n1 - Create an Id \n2 - Login\n3 - Update Detail \n4 - Delete Id\n5 - Exit\n\nEnter your choice : ");
                int ur = Convert.ToInt32(Console.ReadLine());                
                Thread.Sleep(1000);
                Console.Clear();
                if (ur == 1)
                {
                    Console.WriteLine("\n\t\t\t\t\tWelcome to registraion\n\n");
                    Console.Write("Name           : ");
                    string name = Console.ReadLine();
                    dname.Add(name);
                    Console.Write("Age            : ");
                    
                    int age = Convert.ToInt32(Console.ReadLine());
                    while (age > 100 || age < 20)
                    {
                        Console.WriteLine("Try again with a valid age ...");
                        Console.Write("Age            : ");
                        age = Convert.ToInt32(Console.ReadLine());
                    }
                    dage.Add(age);
                    Console.Write("Gender(M/F/T)  : ");
                    string gen = Console.ReadLine();
                    while(gen.ToUpper() != "M"&&gen.ToUpper() != "F"&&gen.ToUpper() !="T")
                    {
                        Console.WriteLine("Try again with the below ones only .... ");
                        Console.Write("Gender(M/F/T)  : ");
                        gen = Console.ReadLine();
                    }
                    dg.Add(gen.ToUpper());
                    Console.Write("Address        : ");
                    dadd.Add(Console.ReadLine());
                    Console.Write("Specialization : ");
                    dsp.Add(Console.ReadLine());
                    Console.Write("Phone number   : ");
                    dph.Add(Convert.ToInt64(Console.ReadLine()));
                    Console.WriteLine("\n\nThanks for registering ....");
                    Thread.Sleep(1000);
                    Console.WriteLine("\n\nYour user id is : " + (name + age));
                    did.Add(name + age);
                    Console.Write("\n\nDo you want to go for Home page (1 - Yes / 2 - Exit) : ");
                    ch = Convert.ToInt32(Console.ReadLine());
                    if (ch == 1)
                    {
                        Console.ForegroundColor = ConsoleColor.Blue;
                        Thread.Sleep(1000);
                        goto x;
                    }
                    else
                    {
                        break;
                    }
                }
                else if(ur==2)
                {
                    Console.Clear();
                    Console.WriteLine("\t\t\t\t\tWelcome to login page \n");
                    Console.Write("\nPlease provide your Id : ");
                    uid = Console.ReadLine();
                    if (dname.Count <= 0)
                    {
                        Console.Clear();
                        Console.WriteLine("You are not registered so register first ...");
                        goto j;
                    }
                    else if(dname.Count>0)
                    {
                        int count = 0;
                        for(int i=0;i<dname.Count;i++)
                        {
                            if (uid == did[i])
                            {
                                count = 1;
                            }
                        }
                        if(count==0)
                        {
                            Console.WriteLine("Your are not Registered ....");
                            Thread.Sleep(3000);
                            goto j;
                        }
                        else
                        {
                            for (int i = 0; i < dname.Count; i++)
                            {
                                if (uid == did[i])
                                {
                                    Console.WriteLine();
                                    Console.WriteLine("Name           : " + dname[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Age            : " + dage[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Gender         : " + dg[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Address        : " + dadd[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Specialization : " + dsp[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Phone number   : " + dph[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Doctor id      : " + did[i] + "\n");
                                }
                            }
                        }
                    }                 
                }
                else if(ur==3)
                {
                    Console.WriteLine("\n\t\t\tWelcome to Updation portal");
                    Console.Write("\n\n Enter your login id : ");
                    string chan = Console.ReadLine();
                    if(did.Count<=0)
                    {
                        Console.Clear();
                        Thread.Sleep(1000);
                        Console.WriteLine("\n\nYou are registered so register first ....\n");
                        goto j;
                    }
                    else if(did.Count>0)
                    {
                        int count = 0;
                        for(int i=0;i<did.Count;i++)
                        {
                            if (chan == did[i])
                            {
                                count = 1;
                            }
                        }
                        if(count==1)
                        {
                            for (int i = 0; i < did.Count; i++)
                            {
                                if (chan == did[i])
                                {
                                    Console.Write("Name             : ");
                                    string name = Console.ReadLine();
                                    dname[i] = name;
                                    Console.Write("Age              : ");
                                    int age = Convert.ToInt32(Console.ReadLine());
                                    while (age > 100)
                                    {
                                        Console.WriteLine("Try again with a valid age ...");
                                        Console.Write("Age              : ");
                                        age = Convert.ToInt32(Console.ReadLine());
                                    }
                                    dage[i] = age;
                                    Console.Write("Gender(M/F/T)    : ");
                                    string gen = Console.ReadLine();
                                    while (gen.ToUpper() != "M" && gen.ToUpper() != "F" && gen.ToUpper() != "T")
                                    {
                                        Console.WriteLine("Try again with the below ones only .... ");
                                        Console.Write("Gender(M/F/T)    : ");
                                        Console.Write("Address          : ");
                                        gen = Console.ReadLine();
                                    }
                                    dg[i] = (gen.ToUpper());
                                    Console.Write("Address          : ");
                                    string addre = Console.ReadLine();
                                    dadd[i] = addre;
                                    Console.Write("Specialization : ");
                                    string sp = Console.ReadLine();
                                    dsp[i] = sp;
                                    Console.Write("Phone number     : ");
                                    long ph = Convert.ToInt64(Console.ReadLine());
                                    dph[i] = ph;
                                    Console.WriteLine(); Thread.Sleep(1000);
                                    Console.WriteLine("Thanks for Updating your details ....\n\n");
                                    Thread.Sleep(1000);
                                    Console.WriteLine("Your new user id is : " + (name + age));
                                    string ids = name + age;
                                    did[i] = ids;

                                }
                            }
                        }
                        else
                        {
                            Console.Clear();
                            Thread.Sleep(1000);
                            Console.WriteLine("\n\nYou are registered so register first ....\n");
                            goto j;
                        }
                    }
                }    
                else if(ur==4)
                {
                    Console.WriteLine("\n\t\t\tWelcome to Updation portal");
                    Console.Write("\n\n Enter your login id : ");
                    string chan = Console.ReadLine();
                    if (did.Count <= 0)
                    {
                        Console.Clear();
                        Thread.Sleep(1000);
                        Console.WriteLine("\n\nYou are registered so register first ....\n");
                        goto j;
                    }
                    else if (did.Count > 0)
                    {
                        int count = 0;
                        for (int i = 0; i < did.Count; i++)
                        {
                            if (chan == did[i])
                            {
                                count = 1;
                            }
                        }
                        if (count == 1)
                        {
                            for (int i = 0; i < did.Count; i++)
                            {
                                if (chan == did[i])
                                {
                                    dname.RemoveAt(i);                                    
                                    dage.RemoveAt(i);
                                    dg.RemoveAt(i);                                    
                                    dadd.RemoveAt(i);                                    
                                    dsp.RemoveAt(i);                                    
                                    dph.RemoveAt(i);
                                    Thread.Sleep(1000);
                                    Console.WriteLine("Your info has been erased ....\n\n");
                                    Thread.Sleep(1000);                         
                                    did.RemoveAt(i);

                                }
                            }
                        }
                        else
                        {
                            Console.Clear();
                            Thread.Sleep(1000);
                            Console.WriteLine("\n\nYou are registered so register first ....\n");
                            goto j;
                        }
                    }                    
                }
                else if (ur == 5)
                {
                    Console.WriteLine("Exiting.......");
                    Thread.Sleep(3000);
                    break;
                }
                else
                {
                    Console.WriteLine("Enter a valid option ...");
                    goto j;
                }
                Thread.Sleep(2000);
                Console.Write("\n\nDo you want to Mainmenu (1 - yes / 2 - Exit): ");
                ch = Convert.ToInt32(Console.ReadLine());
                if (ch == 1)
                {
                    Console.ForegroundColor = ConsoleColor.Blue;
                    goto x;
                }
                else
                {
                    break;
                }
            }
            else if (n == 2)
            {
                Thread.Sleep(1000);
                Console.Clear();      
                Console.ForegroundColor = ConsoleColor.White;
            g:                
                Console.WriteLine("\n\n\t\t\t\t\tWelcome to registration portal for Receptionist\n");               
                Console.WriteLine("\n═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════");
                Console.Write("\n1 - Create an Id \n2 - Login\n3 - Update Detail \n4 - Delete Id\n5 - Exit\n\nEnter your choice : ");
                int ur = Convert.ToInt32(Console.ReadLine());
                Thread.Sleep(1000);
                Console.Clear();
                if (ur == 1)
                {
                    Console.WriteLine("\n\t\t\t\t\tWelcome to registraion\n\n");
                    Console.Write("Name           : ");
                    string name = Console.ReadLine();
                    rname.Add(name);
                    Console.Write("Age            : ");                    
                    int age = Convert.ToInt32(Console.ReadLine());
                    while (age > 100 || age < 20)
                    {
                        Console.WriteLine("Try again with a valid age ...");
                        Console.Write("Age            : ");
                        age = Convert.ToInt32(Console.ReadLine());
                    }
                    rage.Add(age);
                    Console.Write("Gender(M/F/T)  : ");
                    string gen = Console.ReadLine();
                    while (gen.ToUpper() != "M" && gen.ToUpper() != "F" && gen.ToUpper() != "T")
                    {
                        Console.WriteLine("Try again with the below ones only .... ");
                        Console.Write("Gender(M/F/T)  : ");
                        gen = Console.ReadLine();
                    }
                    rg.Add(gen.ToUpper());
                    Console.Write("Address        : ");
                    radd.Add(Console.ReadLine());
                    Console.Write("Phone number   : ");
                    rph.Add(Convert.ToInt64(Console.ReadLine()));
                    Thread.Sleep(1000);
                    Console.WriteLine("\nThanks for registering ....\n\n");                    
                    Thread.Sleep(1000);
                    Console.WriteLine("Your user id is : " + (name + age)+"\n\n");
                    rid.Add(name + age);
                    Console.Write("Do you want to Homepage (1 - yes / 2 - Print Doctor Staff list /3 - Exit): ");
                    ch = Convert.ToInt32(Console.ReadLine());
                    if (ch == 1)
                    {
                        Console.ForegroundColor = ConsoleColor.White;
                        Thread.Sleep(2000);
                        goto x;
                    }
                    else if(ch==2)
                    {
                        if(dname.Count<=0)
                        {
                            Thread.Sleep(1000);
                            Console.WriteLine("\n\nThere are no doctor at present ....");

                        }
                        else
                        {

                            Console.WriteLine("These are the details of doctors");
                            Thread.Sleep(1000);
                            Console.WriteLine("Doctor Name \t\t\t Age \t\t\t Gender \t\t\t Phone Number \t\t\tAddress\t\t\t Doctor Id");
                            for(int i=0;i<dname.Count;i++)
                            {
                                Thread.Sleep(1000);
                                Console.WriteLine(dname[i] + "\t\t" + dage[i] + "\t\t" + dg[i] + "\t\t\t" + dph[i] + "\t\t" + dadd[i] + "\t" + did[i]);
                                Thread.Sleep(1000);
                            }
                        }
                    }
                    else
                    {
                        break;
                    }
                }
                else if(ur==2)
                {
                    Console.Clear();
                    Console.WriteLine("\n\t\t\t\t\tWelcome to Login page\n");
                    Console.Write("\nPlease provide your Id : ");
                    uid = Console.ReadLine();
                    if (rname.Count <= 0)
                    {
                        Console.Clear();
                        Console.WriteLine("You are not registered so register first ...\n");
                        goto g;
                    }
                    else if (rname.Count > 0)
                    {
                        int count = 0;
                        for (int i = 0; i < rname.Count; i++)
                        {
                            if (uid == rid[i])
                            {
                                count = 1;
                            }
                        }
                        if (count == 0)
                        {
                            Console.WriteLine("Your are not Registered ....");
                            Thread.Sleep(3000);
                            goto g;
                        }
                        else
                        {                            
                            Console.Clear();
                            Thread.Sleep(1000);
                            for (int i = 0; i < rname.Count; i++)
                            {
                                if (uid == rid[i])
                                {
                                    Console.WriteLine();
                                    Console.WriteLine("Name           : " + rname[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Age            : " + rage[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Address        : " + radd[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Gender         : " + rg[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Phone number   : " + rph[i] + "\n"); Thread.Sleep(1000);
                                    Console.WriteLine("Receptionist id: " + rid[i] + "\n");
                                }
                            }
                        }
                    }
                    
                    Thread.Sleep(1000);
                    Console.Write("Do you want to Homepage (1 - yes / 2 - Print Doctor Staff list /3 - Exit): ");
                    ch = Convert.ToInt32(Console.ReadLine());
                    if (ch == 1)
                    {
                        Console.ForegroundColor = ConsoleColor.White;
                        Thread.Sleep(2000);
                        goto x;
                    }
                    else if (ch == 2)
                    {
                        if (dname.Count <= 0)
                        {
                            Thread.Sleep(1000);
                            Console.WriteLine("\n\nThere are no doctor at present ....");

                        }
                        else
                        {

                            Console.WriteLine("These are the details of doctors");
                            Thread.Sleep(1000);
                            Console.WriteLine("Doctor Name \t\t\t Age \t\t\t Gender \t\t\t Phone Number \t\t\tAddress\t\t\t Doctor Id");
                            Console.WriteLine("\n═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════\n");
                            for (int i = 0; i < dname.Count; i++)
                            {
                                Thread.Sleep(1000);
                                Console.WriteLine(dname[i] + "\t\t" + dage[i] + "\t\t" + dg[i] + "\t\t\t" + dph[i] + "\t\t" + dadd[i] + "\t" + did[i]);
                                Thread.Sleep(1000);
                            }
                        }
                    }
                    else
                    {
                        break;
                    }
                }
                else if (ur == 3)
                {
                    Console.WriteLine("\n\t\t\tWelcome to Updation portal");
                    Console.Write("\n\n Enter your login id : ");
                    string chan = Console.ReadLine();
                    if (rid.Count <= 0)
                    {
                        Console.Clear();
                        Thread.Sleep(1000);
                        Console.WriteLine("\n\nYou are registered so register first ....\n");
                        goto g;
                    }
                    else if (rid.Count > 0)
                    {
                        int count = 0;
                        for (int i = 0; i < rid.Count; i++)
                        {
                            if (chan == rid[i])
                            {
                                count = 1;
                            }
                        }
                        if (count == 1)
                        {
                            for (int i = 0; i < rid.Count; i++)
                            {
                                if (chan == rid[i])
                                {
                                    Console.Write("Name             : ");
                                    string name = Console.ReadLine();
                                    rname[i] = name;
                                    Console.Write("Age              : ");
                                    int age = Convert.ToInt32(Console.ReadLine());
                                    while (age > 100)
                                    {
                                        Console.WriteLine("Try again with a valid age ...");
                                        Console.Write("Age              : ");
                                        age = Convert.ToInt32(Console.ReadLine());
                                    }
                                    rage[i] = age;
                                    Console.Write("Gender(M/F/T)    : ");
                                    string gen = Console.ReadLine();
                                    while (gen.ToUpper() != "M" && gen.ToUpper() != "F" && gen.ToUpper() != "T")
                                    {
                                        Console.WriteLine("Try again with the below ones only .... ");
                                        Console.Write("Gender(M/F/T)    : ");
                                        Console.Write("Address          : ");
                                        gen = Console.ReadLine();
                                    }
                                    rg[i] = (gen.ToUpper());
                                    Console.Write("Address          : ");
                                    string addre = Console.ReadLine();
                                    radd[i] = addre;                                    
                                    Console.Write("Phone number     : ");
                                    long ph = Convert.ToInt64(Console.ReadLine());
                                    rph[i] = ph;
                                    Console.WriteLine(); Thread.Sleep(1000);
                                    Console.WriteLine("Thanks for Updating your details ....\n\n");
                                    Thread.Sleep(1000);
                                    Console.WriteLine("Your new user id is : " + (name + age));
                                    string ids = name + age;
                                    rid[i] = ids;

                                }
                            }
                        }
                        else
                        {
                            Console.Clear();
                            Thread.Sleep(1000);
                            Console.WriteLine("\n\nYou are registered so register first ....\n");
                            goto g;
                        }
                    }
                }
                else if (ur == 4)
                {
                    Console.WriteLine("\n\t\t\tWelcome to Updation portal");
                    Console.Write("\n\n Enter your login id : ");
                    string chan = Console.ReadLine();
                    if (rid.Count <= 0)
                    {
                        Console.Clear();
                        Thread.Sleep(1000);
                        Console.WriteLine("\n\nYou are registered so register first ....\n");
                        goto g;
                    }
                    else if (rid.Count > 0)
                    {
                        int count = 0;
                        for (int i = 0; i < rid.Count; i++)
                        {
                            if (chan == rid[i])
                            {
                                count = 1;
                            }
                        }
                        if (count == 1)
                        {
                            for (int i = 0; i < rid.Count; i++)
                            {
                                if (chan == rid[i])
                                {
                                    rname.RemoveAt(i);
                                    rage.RemoveAt(i);
                                    rg.RemoveAt(i);
                                    radd.RemoveAt(i);
                                    rph.RemoveAt(i);
                                    Thread.Sleep(1000);
                                    Console.WriteLine("Your info has been erased ....\n\n");
                                    Thread.Sleep(1000);
                                    rid.RemoveAt(i);

                                }
                            }
                        }
                        else
                        {
                            Console.Clear();
                            Thread.Sleep(1000);
                            Console.WriteLine("\n\nYou are registered so register first ....\n");
                            goto g;
                        }
                    }
                }
                else if (ur == 5)
                {
                    Console.WriteLine("Exiting.......");
                    Thread.Sleep(3000);
                    break;
                }
                else
                {
                    Console.WriteLine("Enter a valid option ...");
                    goto g;
                }
                Thread.Sleep(3000);
                Console.Write("\n\nDo you wish to goto Mainmenu press '1' and press '2' to Exit :");
                n = Convert.ToInt32(Console.ReadLine());
                if(n==1)
                {
                    Console.Clear();
                    Thread.Sleep(2000);
                    goto x;
                }
                else
                {
                    break;
                }
            }
            else if (n == 3)
            {
                
                Thread.Sleep(1000);
                Console.Clear();
            l:
                Console.ForegroundColor = ConsoleColor.DarkBlue;
                Console.WriteLine("\n\n\t\t\t\t\tWelcome to Reception");
                Console.WriteLine("\n═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════");
                Console.Write("\n\nHow can I help you ....\n\n1 - Create an Id \n2 - Login\n3 - Update Detail \n4 - Delete Id\n5 - Exit\n\nEnter your choice : ");
                int ur = Convert.ToInt32(Console.ReadLine());
                Thread.Sleep(1000);
                Console.Clear();
                if (ur == 1)
                {
                    Console.WriteLine("\n\t\t\t\t\tWelcome to registraion\n\n");
                    Console.Write("Name             : ");
                    string name = Console.ReadLine();
                    pname.Add(name);
                    Console.Write("Age              : ");                    
                    int age = Convert.ToInt32(Console.ReadLine());
                    while (age > 100)
                    {
                        Console.WriteLine("Try again with a valid age ...");
                        Console.Write("Age              : ");                        
                        age = Convert.ToInt32(Console.ReadLine());
                    }
                    page.Add(age);
                    Console.Write("Gender(M/F/T)    : ");                    
                    string gen = Console.ReadLine();
                    while (gen.ToUpper() != "M" && gen.ToUpper() != "F" && gen.ToUpper() != "T")
                    {
                        Console.WriteLine("Try again with the below ones only .... ");
                        Console.Write("Gender(M/F/T)    : ");
                        Console.Write("Address          : ");
                        gen = Console.ReadLine();
                    }
                    pg.Add(gen.ToUpper());
                    Console.Write("Address          : ");
                    padd.Add(Console.ReadLine());
                    Console.Write("Phone number     : ");
                    long ph= Convert.ToInt64(Console.ReadLine());
                    pph.Add(ph);
                    Console.Write("Purpose of visit : ");
                    string disea= Console.ReadLine();
                    pdis.Add(disea);
                    Console.WriteLine(); Thread.Sleep(1000);
                    Console.WriteLine("Thanks for registering ....\n\n");                    
                    Thread.Sleep(1000);
                    Console.WriteLine("Your user id is : " + (age + ph % 10000));
                    pid.Add(age+ph%10000);
                   q:
                    Console.Write("\n\nDo you want to Mainmenu '1'or visit doctor '2' and press '3' change details : ");
                    ch = Convert.ToInt32(Console.ReadLine());
                    if (ch == 1)
                    {
                        Console.ForegroundColor = ConsoleColor.Magenta;
                        Thread.Sleep(2000);
                        goto x;
                    }
                    else if (ch == 2)
                    {
                        Console.ForegroundColor = ConsoleColor.Green;
                        Console.WriteLine("\nplease wait while we are connecting doctor ...");
                        Thread.Sleep(5000);
                    u:
                        Console.Clear();
                        Console.WriteLine("Doctor  : Hi how are you (Mr/Mis)" + name);
                        Console.ForegroundColor = ConsoleColor.White;
                        Console.Write("Patient : ");
                        pat = Console.ReadLine();
                        Console.ForegroundColor = ConsoleColor.Green;
                        Console.WriteLine("Doctor  : your id " + (age + ph % 10000));
                        Console.ForegroundColor = ConsoleColor.White;
                        Console.Write("Patient : ");
                        pat = Console.ReadLine();
                        Console.ForegroundColor = ConsoleColor.Green;
                        Console.WriteLine("Doctor  : your disease " + disea);
                        Console.ForegroundColor = ConsoleColor.White;
                        Console.Write("Patient : ");
                        pat = Console.ReadLine();
                        while (doc != "You may leave now" && pat != "Thank you")
                        {
                            Console.ForegroundColor = ConsoleColor.Green;
                            Console.Write("Doctor  : ");
                            doc = Console.ReadLine();
                            Thread.Sleep(2000);
                            Console.ForegroundColor = ConsoleColor.White;
                            Console.Write("Patient : ");
                            pat = Console.ReadLine();
                            Thread.Sleep(2000);
                        }
                        Console.Write("Do you want to visit doctor again ('1') or proceed with the formaties ('2') : ");
                        int v = Convert.ToInt32(Console.ReadLine());
                        if (v == 1)
                        {
                            goto u;
                        }
                        else
                        {
                            Console.Write("\n\nPlease provide your Id : ");
                            uid1 = Convert.ToInt64(Console.ReadLine());
                            for (int i = 0; i < pid.Count; i++)
                            {
                                if (uid1 == pid[i])
                                {
                                    Console.WriteLine("\nThese are the medicines you need are as follows ....");
                                    if (pdis[i].ToLower() == "kidney")
                                    {
                                        Console.WriteLine("\n\nBeta Blockers.\n\nDiuretics.\n\nFinerenone.\n\nInsulin.\n\nMetformin.\n\nStatins.\n\nAce.\nGLP-1.");
                                        med.Add("Beta Blockers"); med.Add("Diuretics");
                                        med.Add("Finerenone"); med.Add("Insulin");
                                        med.Add("Metformin"); med.Add("Statins");
                                        med.Add("Ace"); med.Add("GLP - 1.");
                                    }
                                    else if (pdis[i].ToLower() == "lungs")
                                    {
                                        Console.WriteLine("\n\nAclidinium.\n\nArformoterol.\n\nFormoterol.\n\nGlycopyrrolate.\n\nIndacaterol. \n\nOlodaterol.");
                                        med.Add("Aclidinium"); med.Add("Arformoterol");
                                        med.Add("Glycopyrrolate"); med.Add("Formoterol");
                                        med.Add("Indacaterol"); med.Add("Olodaterol");
                                    }
                                    else if (pdis[i].ToLower() == "heart")
                                    {
                                        Console.WriteLine("\nAcebutolol (Sectral).\n\nAtenolol (Tenormin).\n\nBetaxolol (Kerlone).\n\nBisoprolol/hydrochlorothiazide (Ziac).\n\nBisoprolol (Zebeta).\n\nMetoprolol (Lopressor, Toprol XL).");
                                        med.Add("Acebutolol (Sectral)"); med.Add("Atenolol (Tenormin)");
                                        med.Add("Betaxolol (Kerlone)"); med.Add("Bisoprolol/hydrochlorothiazide (Ziac)");
                                        med.Add("Bisoprolol (Zebeta)"); med.Add("Metoprolol (Lopressor, Toprol XL)");
                                    }
                                    else if (pdis[i].ToLower() == "ent")
                                    {
                                        Console.WriteLine("\nFluticasone nasal preparations.\n\nGentamicin ear drops.\n\nHydrocortisone muco-adhesive tablets for mouth ulcers.\n\nIpratropium nasal spray (Rinaspray)");
                                        med.Add("Fluticasone nasal preparations");
                                        med.Add("Gentamicin ear drops");
                                        med.Add("Acebutolol (Sectral)"); med.Add("Atenolol (Tenormin)");
                                        med.Add("Hydrocortisone muco-adhesive tablets for mouth ulcers");
                                        med.Add("Ipratropium nasal spray (Rinaspray)");
                                    }
                                    else
                                    {
                                        Console.WriteLine("\nAcetaminophen.\n\nAtorvastatin.\n\nAmoxicillin.\n\nLisinopril.\n\nLevothyroxine.");
                                        med.Add("Atorvastatin");
                                        med.Add("Amoxicillin");
                                        med.Add("Lisinopril "); med.Add("Betaxolol (Kerlone)");
                                        med.Add("Levothyroxine");
                                        med.Add("Acetaminophen");

                                    }
                                }
                            }
                            Console.Write("Would you like to buy the mediciences here yes or no : ");
                            string y = Console.ReadLine();
                            if (y.ToUpper() == "YES")
                            {
                                Console.Clear();
                                Thread.Sleep(3000);
                                Console.WriteLine("\t\t\t\t\tBill Details ");
                                Console.WriteLine("\n═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════");
                                for (int i = 0; i < pname.Count; i++)
                                {
                                    if (uid1 == pid[i])
                                    {
                                        Console.WriteLine();
                                        Console.WriteLine("Name           : " + pname[i] + "\n"); Thread.Sleep(1000);
                                        Console.WriteLine("Age            : " + page[i] + "\n"); Thread.Sleep(1000);
                                        Console.WriteLine("Address        : " + padd[i] + "\n"); Thread.Sleep(1000);
                                        Console.WriteLine("Gender         : " + pg[i] + "\n"); Thread.Sleep(1000);
                                        Console.WriteLine("Phone number   : " + pph[i] + "\n"); Thread.Sleep(1000);
                                        Console.WriteLine("Patient id     : " + pid[i] + "\n");
                                    }
                                }
                                Console.WriteLine("\n═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════\n\n");
                                Console.WriteLine("Medicine name\t\t\t\tQuantity\t\t\t\tTotal");
                                int tot = 2000;
                                for (int i = 0; i < med.Count; i++)
                                {
                                    Thread.Sleep(3000);
                                    Console.WriteLine(med[i] + "\t\t\t\t10\t\t\t\t\tRs." + qu[i] * 10);
                                    tot = tot + (qu[i] * 10);
                                    med.RemoveAt(0);
                                }
                                Console.WriteLine("\n═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════");
                                Console.WriteLine("\t\t\t\t\t\t\tTotal Amount = Rs." + tot);
                            }


                        }
                    }
                    else if(ch==3)
                    {
                        Console.Write("\n\n Enter your login id : ");
                        long chan = Convert.ToInt64(Console.ReadLine());
                        for(int i=0;i<pid.Count;i++)
                        {
                            if (chan== pid[i])
                            {
                                Console.Write("Name             : ");
                                name = Console.ReadLine();
                                pname[i]=name;
                                Console.Write("Age              : ");
                                age = Convert.ToInt32(Console.ReadLine());
                                while (age > 100)
                                {
                                    Console.WriteLine("Try again with a valid age ...");
                                    Console.Write("Age              : ");
                                    age = Convert.ToInt32(Console.ReadLine());
                                }
                                page[i]=age;
                                Console.Write("Gender(M/F/T)    : ");
                                gen = Console.ReadLine();
                                while (gen.ToUpper() != "M" && gen.ToUpper() != "F" && gen.ToUpper() != "T")
                                {
                                    Console.WriteLine("Try again with the below ones only .... ");
                                    Console.Write("Gender(M/F/T)    : ");
                                    Console.Write("Address          : ");
                                    gen = Console.ReadLine();
                                }
                                pg[i]=(gen.ToUpper());
                                Console.Write("Address          : ");
                                string addre=Console.ReadLine();
                                padd[i] = addre;
                                Console.Write("Phone number     : ");
                                ph = Convert.ToInt64(Console.ReadLine());
                                pph[i] = ph;
                                Console.Write("Purpose of visit : ");
                                string pur=Console.ReadLine();
                                pdis[i]=pur;
                                Console.WriteLine(); Thread.Sleep(1000);
                                Console.WriteLine("Thanks for registering ....\n\n");
                                Thread.Sleep(1000);
                                Console.WriteLine("Your user id is : " + (age + ph % 10000));
                                long ids= age + ph % 10000;
                                pid[i] = ids;
                                goto q; 
                            }
                        }
                    }
                }
                else if(ur==2)
                {
                    Console.Write("\nPlease provide your Id : ");
                    uid1 = Convert.ToInt64(Console.ReadLine());
                    if (pname.Count <= 0)
                    {
                        Console.Clear();
                        Console.WriteLine("You are not registered so register first ...");
                        goto l;
                    }
                    Console.Clear();
                    Thread.Sleep(1000);
                    int count = 0;
                    for (int i = 0; i < pname.Count; i++)
                    {
                        if (uid1 == pid[i])
                        {
                            Console.WriteLine();
                            Console.WriteLine("Name           : " + pname[i] + "\n"); Thread.Sleep(1000);
                            Console.WriteLine("Age            : " + page[i] + "\n"); Thread.Sleep(1000);
                            Console.WriteLine("Address        : " + padd[i] + "\n"); Thread.Sleep(1000);
                            Console.WriteLine("Gender         : " + pg[i] + "\n"); Thread.Sleep(1000);
                            Console.WriteLine("Phone number   : " + pph[i] + "\n"); Thread.Sleep(1000);
                            Console.WriteLine("Patient id     : " + pid[i] + "\n");
                            count = i;
                        }
                    }
                    Console.Write("Do you want to Mainmenu '1'or  visit doctor '2' : ");
                    int chn = Convert.ToInt32(Console.ReadLine());
                    if (chn == 1)
                    {
                        Console.ForegroundColor = ConsoleColor.Blue;
                        goto x;
                    }
                    else if (chn == 2)
                    {
                        Console.ForegroundColor = ConsoleColor.Green;
                        Console.WriteLine("\nplease wait while we are connecting doctor ...");
                        Thread.Sleep(5000);
                    q:
                        Console.Clear();                        
                        Console.WriteLine("Doctor  : Hi how are you (Mr/Mis) " + pname[count]);
                        Console.ForegroundColor = ConsoleColor.White;
                        Console.Write("Patient : ");
                        pat = Console.ReadLine();
                        Console.ForegroundColor = ConsoleColor.Green;
                        Console.WriteLine("Doctor  : your id " + pid[count]);
                        Console.ForegroundColor = ConsoleColor.White;
                        Console.Write("Patient : ");
                        pat = Console.ReadLine();
                        Console.ForegroundColor = ConsoleColor.Green;
                        Console.WriteLine("Doctor  : your disease " + pdis[count]);
                        doc = Console.ReadLine();
                        Console.ForegroundColor = ConsoleColor.White;
                        Console.Write("Patient : ");
                        pat = Console.ReadLine();
                        while (doc != "You may leave now" && pat != "Thank you")
                        {
                            Console.ForegroundColor = ConsoleColor.Green;
                            Console.Write("Doctor  : ");
                            doc = Console.ReadLine();
                            Thread.Sleep(2000);
                            Console.ForegroundColor = ConsoleColor.White;
                            Console.Write("Patient : ");
                            pat = Console.ReadLine();
                            Thread.Sleep(2000);
                        }
                        Console.Write("Do you want to visit doctor again ('1') or proceed with the formaties ('2') :");
                        int v = Convert.ToInt32(Console.ReadLine());
                        if (v == 1)
                        {
                            goto q;
                        }
                        else
                        {
                            Console.Write("\nPlease provide your Id : ");
                            uid1 = Convert.ToInt64(Console.ReadLine());
                            for (int i = 0; i < pid.Count; i++)
                            {
                                if (uid1 == pid[i])
                                {
                                    Console.WriteLine("These are the medicines you need are as follows ....");
                                    if (pdis[i].ToLower() == "kidney")
                                    {
                                        Console.WriteLine("\nBeta Blockers.\nDiuretics.\nFinerenone.\nInsulin.\nMetformin.\nStatins.\nAce.\nGLP-1.");
                                        med.Add("Beta Blockers"); med.Add("Diuretics");
                                        med.Add("Finerenone"); med.Add("Insulin");
                                        med.Add("Metformin"); med.Add("Statins");
                                        med.Add("Ace"); med.Add("GLP - 1.");
                                    }
                                    else if (pdis[i].ToLower() == "lungs")
                                    {
                                        Console.WriteLine("\nAclidinium.\nArformoterol. \nFormoterol. \nGlycopyrrolate. \nIndacaterol. \nOlodaterol.");
                                        med.Add("Aclidinium"); med.Add("Arformoterol");
                                        med.Add("Glycopyrrolate"); med.Add("Formoterol");
                                        med.Add("Indacaterol"); med.Add("Olodaterol");
                                    }
                                    else if (pdis[i].ToLower() == "heart")
                                    {
                                        Console.WriteLine("Acebutolol (Sectral)\nAtenolol (Tenormin)\nBetaxolol (Kerlone)\nBisoprolol/hydrochlorothiazide (Ziac)\nBisoprolol (Zebeta)\nMetoprolol (Lopressor, Toprol XL)");
                                        med.Add("Acebutolol (Sectral)"); med.Add("Atenolol (Tenormin)");
                                        med.Add("Betaxolol (Kerlone)"); med.Add("Bisoprolol/hydrochlorothiazide (Ziac)");
                                        med.Add("Bisoprolol (Zebeta)"); med.Add("Metoprolol (Lopressor, Toprol XL)");
                                    }
                                    else if (pdis[i].ToLower() == "ent")
                                    {
                                        Console.WriteLine("Fluticasone nasal preparations.\nGentamicin ear drops.\nHydrocortisone muco-adhesive tablets for mouth ulcers.\nIpratropium nasal spray (Rinaspray)");
                                        med.Add("Fluticasone nasal preparations");
                                        med.Add("Gentamicin ear drops");
                                        med.Add("Acebutolol (Sectral)"); med.Add("Atenolol (Tenormin)");
                                        med.Add("Hydrocortisone muco-adhesive tablets for mouth ulcers");
                                        med.Add("Ipratropium nasal spray (Rinaspray)");
                                    }
                                    else
                                    {
                                        Console.WriteLine("Acetaminophen\nAtorvastatin\nAmoxicillin\nLisinopril \nLevothyroxine");
                                        med.Add("Atorvastatin");
                                        med.Add("Amoxicillin");
                                        med.Add("Lisinopril "); med.Add("Betaxolol (Kerlone)");
                                        med.Add("Levothyroxine");
                                        med.Add("Acetaminophen");

                                    }
                                }
                            }
                            Console.Write("Would you like to buy the mediciences here yes or no : ");
                            string y = Console.ReadLine();
                            if (y.ToUpper() == "YES")
                            {
                                Console.Clear();
                                Thread.Sleep(3000);
                                Console.WriteLine("\t\t\t\t\tBill Details ");
                                Console.WriteLine("\n═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════");
                                for (int i = 0; i < pname.Count; i++)
                                {
                                    if (uid1 == pid[i])
                                    {
                                        Console.WriteLine();
                                        Console.WriteLine("Name           : " + pname[i] + "\n"); Thread.Sleep(1000);
                                        Console.WriteLine("Age            : " + page[i] + "\n"); Thread.Sleep(1000);
                                        Console.WriteLine("Address        : " + padd[i] + "\n"); Thread.Sleep(1000);
                                        Console.WriteLine("Gender         : " + pg[i] + "\n"); Thread.Sleep(1000);
                                        Console.WriteLine("Phone number   : " + pph[i] + "\n"); Thread.Sleep(1000);
                                        Console.WriteLine("Patient id     : " + pid[i] + "\n");
                                    }
                                }
                                Console.WriteLine("\n═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════\n\n");
                                Console.WriteLine("Medicine name\t\t\t\tQuantity\t\t\tTotal\n");
                                Console.WriteLine("\n═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════");
                                int tot = 2000;
                                for (int i = 0; i < med.Count; i++)
                                {
                                    Thread.Sleep(2000);
                                    Console.WriteLine("\n"+med[i] + "\t\t\t\t10\t\t\t\t\tRs." + qu[i] * 10);
                                    tot = tot + (qu[i] * 10);                                    
                                }
                                Console.WriteLine("\n═════════════════════════════════════════════════════════════════════════════════════════════════════════════════════");
                                Console.WriteLine("\t\t\t\t\t\t\t\tTotal Amount = Rs. " + tot);
                            }
                        }
                    }
                }
                else if (ur == 3)
                {
                    Console.WriteLine("\n\t\t\tWelcome to Updation portal");
                    Console.Write("\n\n Enter your login id : ");
                    long chan =Convert.ToInt64(Console.ReadLine());
                    if (pid.Count <= 0)
                    {
                        Console.Clear();
                        Thread.Sleep(1000);
                        Console.WriteLine("\n\nYou are registered so register first ....\n");
                        goto l;
                    }
                    else if (pid.Count > 0)
                    {
                        int count = 0;
                        for (int i = 0; i < pid.Count; i++)
                        {
                            if (chan == pid[i])
                            {
                                count = 1;
                            }
                        }
                        if (count == 1)
                        {
                            for (int i = 0; i < pid.Count; i++)
                            {
                                if (chan == pid[i])
                                {
                                    Console.Write("Name             : ");
                                    string name = Console.ReadLine();
                                    pname[i] = name;
                                    Console.Write("Age              : ");
                                    int age = Convert.ToInt32(Console.ReadLine());
                                    while (age > 100)
                                    {
                                        Console.WriteLine("Try again with a valid age ...");
                                        Console.Write("Age              : ");
                                        age = Convert.ToInt32(Console.ReadLine());
                                    }
                                    page[i] = age;
                                    Console.Write("Gender(M/F/T)    : ");
                                    string gen = Console.ReadLine();
                                    while (gen.ToUpper() != "M" && gen.ToUpper() != "F" && gen.ToUpper() != "T")
                                    {
                                        Console.WriteLine("Try again with the below ones only .... ");
                                        Console.Write("Gender(M/F/T)    : ");
                                        Console.Write("Address          : ");
                                        gen = Console.ReadLine();
                                    }
                                    pg[i] = (gen.ToUpper());
                                    Console.Write("Address          : ");
                                    string addre = Console.ReadLine();
                                    padd[i] = addre;
                                    Console.Write("Purpose of visit : ");
                                    string sp = Console.ReadLine();
                                    pdis[i] = sp;
                                    Console.Write("Phone number     : ");
                                    long ph = Convert.ToInt64(Console.ReadLine());
                                    pph[i] = ph;
                                    Console.WriteLine(); Thread.Sleep(1000);
                                    Console.WriteLine("Thanks for Updating your details ....\n\n");
                                    Thread.Sleep(1000);
                                    Console.WriteLine("Your new user id is : " + (age + ph % 10000));
                                    long ids = (age + ph % 10000);
                                    pid[i] = ids;

                                }
                            }
                        }
                        else
                        {
                            Console.Clear();
                            Thread.Sleep(1000);
                            Console.WriteLine("\n\nYou are registered so register first ....\n");
                            goto l;
                        }
                    }
                }
                else if (ur == 4)
                {
                    Console.WriteLine("\n\t\t\tWelcome to Updation portal");
                    Console.Write("\n\n Enter your login id : ");
                    long chan = Convert.ToInt32(Console.ReadLine());
                    if (pid.Count <= 0)
                    {
                        Console.Clear();
                        Thread.Sleep(1000);
                        Console.WriteLine("\n\nYou are registered so register first ....\n");
                        goto l;
                    }
                    else if (pid.Count > 0)
                    {
                        int count = 0;
                        for (int i = 0; i < pid.Count; i++)
                        {
                            if (chan == pid[i])
                            {
                                count = 1;
                            }
                        }
                        if (count == 1)
                        {
                            for (int i = 0; i < pid.Count; i++)
                            {
                                if (chan == pid[i])
                                {
                                    pname.RemoveAt(i);
                                    page.RemoveAt(i);
                                    pg.RemoveAt(i);
                                    padd.RemoveAt(i);
                                    pdis.RemoveAt(i);
                                    pph.RemoveAt(i);
                                    Thread.Sleep(1000);
                                    Console.WriteLine("Your info has been erased ....\n\n");
                                    Thread.Sleep(1000);
                                    pid.RemoveAt(i);

                                }
                            }
                        }
                        else
                        {
                            Console.Clear();
                            Thread.Sleep(1000);
                            Console.WriteLine("\n\nYou are registered so register first ....\n");
                            goto l;
                        }
                    }
                }
                else if(ur==5)
                {
                    Console.WriteLine("Exiting.......");
                    Thread.Sleep(3000);
                    break;
                }
                else
                {
                    Console.WriteLine("Enter a valid option ...");
                    goto l;
                }
                Thread.Sleep(5000);
                Console.Write("Do you wish to goto mainmenu type yes else exit : ");
                string ad = Console.ReadLine();
                if (ad.ToUpper() == "YES")
                {
                    goto x;
                }
                break;
            }
            else
            {
                Console.WriteLine("\nExiting .....");
                Thread.Sleep(3000);
                break;
            }
        }
        if(n>4 || n<1)
        {
            Console.Clear();
            Thread.Sleep(2000);
            Console.WriteLine("\nplease choose between the below option ...");
            goto x;
        }
        Console.WriteLine("\n\nThank you for visiting ....");
        Console.WriteLine();
    }
}
