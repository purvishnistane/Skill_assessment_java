import java.util.Scanner;
class Admin
{
    Scanner sc=new Scanner(System.in);
    static String Admin_array[][]=new String[100][2];
    static
    {
        Admin_array[0][0]="ARP";
        Admin_array[0][1]="4269";
        Admin_array[1][0]="IAM";
        Admin_array[1][1]="5564";
        Admin_array[2][0]="MMP";
        Admin_array[2][1]="7896";
    }
    static class Admin_Login extends Admin
    {
        Student_Signup s=new Student_Signup();
        void  Admin_login()
        {
            boolean flag=true;
            System.out.print("Enter Admin Username: ");
            String username=sc.next().trim();
            System.out.print("Enter Admin Password: ");
            String password=sc.next().trim();
            for(int i=0;i< Admin.Admin_array.length;i++)
            {
                if(Admin.Admin_array[i][0]!=null && Admin.Admin_array[i][0].equals(username))
                {
                    flag=false;
                    if(Admin.Admin_array[i][1].equals(password))
                    {
                        System.out.println("Admin Successfully Logged In");
                        System.out.print("Do you want to sign-up Student(S) or Update MCQ's(U) or Exit(E) (S/U/E): ");
                        char choice=sc.next().charAt(0);
                        if(choice=='S' || choice=='s')
                        {
                            s.sign_up();
                        }
                        else if(choice=='E' || choice=='e')
                        {
                            System.exit(0);
                        }
                        else if(choice=='U' || choice=='u')
                        {
                            new UpdateMCQ();
                        }
                        else
                        {
                            System.out.println("Invalid Choice");
                            this.Admin_login();
                        }
                        //Call question change method from admin class
                        break;
                    }
                    else
                    {
                        System.out.println("Enter Valid Username or Password!!");
                    }
                }
            }
            if(flag)
            {
                System.out.println("Enter Valid Username or Password!!");
                this.Admin_login();
            }
        }
        void sign_up()
        {
                // We have removed instance block just for checking
                System.out.print("Do You Want to Sign Up Student(Y/N):");
                char choice=sc.next().charAt(0);
                if(choice=='Y' || choice=='y')
                {
                    s.sign_up();
                }
                else if (choice=='N' || choice=='n')
                {

                }
                else
                {
                    System.out.println("Invalid Choice");
                }

        }
    }
    static class UpdateMCQ extends Questions
    {
        {
            Questions.Add_MCQ.physics_update_question();
            Questions.Add_MCQ.maths_update_question();
            Questions.Add_MCQ.java_update_question();
        }
        {
            System.out.println("Which Subject MCQ do you want to update?(P/J/M)");
            char choice= sc.next().charAt(0);
            choice=Character.toLowerCase(choice);
            if(choice=='p' || choice=='j' || choice=='m')
            {
                int medium=new Test().test();
                updateMCQ(choice,medium);
            }
            else
            {
                System.out.println("Invalid Choice");
                new UpdateMCQ();
            }
        }
        void  updateMCQ(char choice,int medium)
        {

            int update_question;
            char choice1;
            Questions.Add_MCQ am=new Questions.Add_MCQ();
            switch (choice)
            {
                case 'p':
                    switch(medium)
                    {
                        case 1:
                            for (int i=0;i<10;i++)
                            {
                                System.out.println(Questions.question_physics[i]);
                            }
                            System.out.println("Which MCQ do you want to update ?");
                            update_question=sc.nextInt();
                            if(update_question<1 || update_question>10)
                            {
                                System.out.println("Invalid Choice!!");
                                updateMCQ(choice, medium);
                            }
                            sc.nextLine();
                            System.out.println("Enter the new question at " + update_question);
                            question_physics[update_question-1] = sc.nextLine();
                            System.out.println("Do you want to update more questions(Y/N): ");
                            choice1=sc.next().charAt(0);
                            choice1=Character.toUpperCase(choice1);
                            if(choice1=='Y')
                            {
                                updateMCQ(choice, medium);
                            }
                            break;
                        case 2:
                            for (int i=10;i<20;i++)
                            {
                                System.out.println(Questions.question_physics[i]);
                            }
                            System.out.println("Which MCQ do you want to update ?");
                            update_question=sc.nextInt();
                            if(update_question<1 || update_question>10)
                            {
                                System.out.println("Invalid Choice!!");
                                updateMCQ(choice, medium);
                            }
                            sc.nextLine();
                            System.out.println("Enter the new question at " + update_question);
                            question_physics[9+update_question] = sc.nextLine();
                            System.out.println("Do you want to update more questions(Y/N): ");
                            choice1=sc.next().charAt(0);
                            choice1=Character.toUpperCase(choice1);
                            if(choice1=='Y')
                            {
                                updateMCQ(choice, medium);
                            }
                            break;
                        case 3:
                            for (int i=20;i<30;i++)
                            {
                                System.out.println(Questions.question_physics[i]);
                            }
                            System.out.println("Which MCQ do you want to update ?");
                            update_question=sc.nextInt();
                            if(update_question<1 || update_question>10)
                            {
                                System.out.println("Invalid Choice!!");
                                updateMCQ(choice, medium);
                            }
                            sc.nextLine();
                            System.out.println("Enter the new question at " + update_question);
                            question_physics[19+update_question] = sc.nextLine();
                            System.out.println("Do you want to update more questions(Y/N): ");
                            choice1=sc.next().charAt(0);
                            choice1=Character.toUpperCase(choice1);
                            if(choice1=='Y')
                            {
                                updateMCQ(choice, medium);
                            }
                            break;
                    }
                    break;
                case 'j':
                    switch(medium)
                    {
                        case 1:
                            for (int i=0;i<10;i++)
                            {
                                System.out.println(Questions.question_java[i]);
                            }
                            System.out.println("Which MCQ do you want to update ?");
                            update_question=sc.nextInt();
                            if(update_question<1 || update_question>10)
                            {
                                System.out.println("Invalid Choice!!");
                                updateMCQ(choice, medium);
                            }
                            sc.nextLine();
                            System.out.println("Enter the new question at " + update_question);
                            question_java[update_question-1] = sc.nextLine();
                            System.out.println("Do you want to update more questions(Y/N): ");
                            choice1=sc.next().charAt(0);
                            choice1=Character.toUpperCase(choice1);
                            if(choice1=='Y')
                            {
                                updateMCQ(choice, medium);
                            }
                            break;
                        case 2:
                            for (int i=10;i<20;i++)
                            {
                                System.out.println(Questions.question_java[i]);
                            }
                            System.out.println("Which MCQ do you want to update ?");
                            update_question=sc.nextInt();
                            if(update_question<1 || update_question>10)
                            {
                                System.out.println("Invalid Choice!!");
                                updateMCQ(choice, medium);
                            }
                            sc.nextLine();
                            System.out.println("Enter the new question at " + update_question);
                            question_java[9+update_question] = sc.nextLine();
                            System.out.println("Do you want to update more questions(Y/N): ");
                            choice1=sc.next().charAt(0);
                            choice1=Character.toUpperCase(choice1);
                            if(choice1=='Y')
                            {
                                updateMCQ(choice, medium);
                            }
                            break;
                        case 3:
                            for (int i=20;i<30;i++)
                            {
                                System.out.println(Questions.question_java[i]);
                            }
                            System.out.println("Which MCQ do you want to update ?");
                            update_question=sc.nextInt();
                            if(update_question<1 || update_question>10)
                            {
                                System.out.println("Invalid Choice!!");
                                updateMCQ(choice, medium);
                            }
                            sc.nextLine();
                            System.out.println("Enter the new question at " + update_question);
                            question_java[19+update_question] = sc.nextLine();
                            System.out.println("Do you want to update more questions(Y/N): ");
                            choice1=sc.next().charAt(0);
                            choice1=Character.toUpperCase(choice1);
                            if(choice1=='Y')
                            {
                                updateMCQ(choice, medium);
                            }
                            break;
                    }
                    break;
                case 'm':
                    switch(medium)
                    {
                        case 1:
                            for (int i=0;i<10;i++)
                            {
                                System.out.println(Questions.question_maths[i]);
                            }
                            System.out.println("Which MCQ do you want to update ?");
                            update_question=sc.nextInt();
                            if(update_question<1 || update_question>10)
                            {
                                System.out.println("Invalid Choice!!");
                                updateMCQ(choice, medium);
                            }
                            sc.nextLine();
                            System.out.println("Enter the new question at " + update_question);
                            question_maths[update_question-1] = sc.nextLine();
                            System.out.println("Do you want to update more questions(Y/N): ");
                            choice1=sc.next().charAt(0);
                            choice1=Character.toUpperCase(choice1);
                            if(choice1=='Y')
                            {
                                updateMCQ(choice, medium);
                            }
                            break;
                        case 2:
                            for (int i=10;i<20;i++)
                            {
                                System.out.println(Questions.question_maths[i]);
                            }
                            System.out.println("Which MCQ do you want to update ?");
                            update_question=sc.nextInt();
                            if(update_question<1 || update_question>10)
                            {
                                System.out.println("Invalid Choice!!");
                                updateMCQ(choice, medium);
                            }
                            sc.nextLine();
                            System.out.println("Enter the new question at " + update_question);
                            question_maths[9+update_question] = sc.nextLine();
                            System.out.println("Do you want to update more questions(Y/N): ");
                            choice1=sc.next().charAt(0);
                            choice1=Character.toUpperCase(choice1);
                            if(choice1=='Y')
                            {
                                updateMCQ(choice, medium);
                            }
                            break;
                        case 3:
                            for (int i=20;i<30;i++)
                            {
                                System.out.println(Questions.question_maths[i]);
                            }
                            System.out.println("Which MCQ do you want to update ?");
                            update_question=sc.nextInt();
                            if(update_question<1 || update_question>10)
                            {
                                System.out.println("Invalid Choice!!");
                                updateMCQ(choice, medium);
                            }
                            sc.nextLine();
                            System.out.println("Enter the new question at " + update_question);
                            question_maths[19+update_question] = sc.nextLine();
                            System.out.println("Do you want to update more questions(Y/N): ");
                            choice1=sc.next().charAt(0);
                            choice1=Character.toUpperCase(choice1);
                            if(choice1=='Y')
                            {
                                updateMCQ(choice, medium);
                            }
                            break;
                    }
                    break;
            }
        }
    }
    static class Student_Signup extends Student
    {
        int count1=0;
        void sign_up()
        {
            if(count1==0)    // We have initialized count1 variable with 0 value which on going to if(Student_password.length()!=4) if this condition is satisfied then the if block will be executed and will get message of error and will call again the same method with incrementing the count++ and now it will go in else block with message of given in that else block.
            {
                System.out.println("Enter Student Sign-Up Details");
            }
            else
            {
                System.out.println("Please Enter valid Student Sign-Up Details");
            }
            int count=0;
            System.out.println("Enter new Student Username: ");
            String Student_username=sc.next().trim();
            System.out.println("Enter new Student Password: ");
            String Student_password = sc.next().trim();
            if(Student_password.length()!=4)
            {
                System.out.println("Password must be of 4 Digit.");
                count1++;
                this.sign_up();
            }
            for(int i=0;i< student.length;i++)
            {
                if(count!=1 && student[i][1]==null ) // After taking count!=1 means when student is added once then it shouldn't be added next time while compiler completing it's loop
                {
                    count++;
                    student[i][0] = Student_username;
                    student[i][1] = Student_password;
                }
            }
            Admin.Admin_Login adl= new Admin_Login();
            adl.sign_up();
        }
    }
    //MAke question change method
}
class Student_Login extends Student
{
    Subject sub=new Subject();
    boolean flag1=true;
    boolean flag2=true;
    void check_login()
    {
        System.out.println("Enter login Details.");
        {
            System.out.print("Enter Student Username: ");
            String Student_user=sc.next().trim();
            System.out.print("Enter Student Password: ");
            String Student_pass=sc.next().trim();
            for(int i=0;i< student.length;i++)
            {
                if( student[i][0]!=null && student[i][0].equals(Student_user) )
                {
                    if(Student_pass.length()==4){
                        //We have removed -1 from below length condition
                        for (int i1 = 0; i1 < Student_pass.length(); i1++) {
                            if(Student_pass.charAt(i1)<'0' && Student_pass.charAt(i1)>'9'){
                                flag1=false;
                            }
                        }
                    }
                    if(flag1)
                    {
                        if(Student_pass.equals(student[i][1]))   // The 2nd index on student[i][1]) is 1 because we have stored password on 1th index.
                        {
                            System.out.println("!!!!!WARNING!!!!!");
                            System.out.println("After starting the test and Skipping question You are not able to Go back to the previous Question");
                            sub.sub();
                            break;
                        }
                        else
                        {
                            flag2=false;
                        }
                    }
                    else{
                        System.out.println("Password must be of 4 characters and all digits");
                        this.check_login();
                    }
                }
            }
            if(flag2==false)
            {
                System.out.println("Enter valid Username or Password!!");
                this.check_login();
            }
        }

    }
}
class Student
{
    Scanner sc=new Scanner(System.in);
    static String [][] student=new String[1000][2];
    int [][] test_complete_answers = new int[1000][2];
}
class Subject
{
    Scanner sc= new Scanner(System.in);
    Test t=new Test();
    Questions.Add_MCQ am=new Questions.Add_MCQ();
    {
        Questions.Add_MCQ.maths_update_question();
        Questions.Add_MCQ.maths_update_option();
        Questions.Add_MCQ.maths_update_answer();
        Questions.Add_MCQ.physics_update_question();
        Questions.Add_MCQ.physics_update_options();
        Questions.Add_MCQ.physics_update_answer();
        Questions.Add_MCQ.java_update_question();
        Questions.Add_MCQ.java_update_option();
        Questions.Add_MCQ.java_update_answer();
    }
    int ch;
    int c=0;
    int correct=0;
    int incorrect=0;
    void sub()
    {
        System.out.println("Enter your choice of subject \n1. for java \n2. for maths \n3. for physics");
        ch= sc.nextInt();
        switch(ch){
            case 1:
                java(t.test());
                break;
            case 2:
                maths(t.test());
                break;
            case 3:
                phy(t.test());
                break;
            default:
                System.out.println("Enter valid choice");
                sub();
        }
    }
    void java(int level)
    {
        if(level==1)
        {
            for(int i=0;i<10;i++)
            {
                java_test_display(i);
            }
            System.out.println(correct);
            System.out.println(incorrect);
        }
        else if (level==2)
        {
            for(int i=10;i<20;i++)
            {
                java_test_display(i);
            }
            System.out.println(correct);
            System.out.println(incorrect);
        }
        else
        {
            for(int i=20;i<30;i++)
            {
                java_test_display(i);
            }
            System.out.println(correct);
            System.out.println(incorrect);
        }
    }
    void java_test_display(int i)
    {
        if(c==0)
        {
            System.out.println("Please enter choice in form of Integer");
            c++;
        }
        if(Questions.question_java[i]!=null)
        {
            System.out.println(Questions.question_java[i]);
            for (int j = 0; j < 4; j++) {
                System.out.print(Questions.option_java[i][j]);
                System.out.print("   ");
            }
            int choice = sc.nextInt();
            if (choice != 1 && choice != 2 && choice != 3 && choice != 4) {
                System.out.println("Invalid Choice");
                java_test_display(i);
            }
            else
            {
                if(Questions.answer_java[i].equals(Questions.option_java[i][choice-1]))
                {
                    correct++;
                }
                else
                {
                    incorrect++;
                }
            }
        }
    }
    void maths(int level)
    {
        if(level==1)
        {
            for(int i=0;i<10;i++)
            {
                math_test_display(i);
            }
            System.out.println(correct);
            System.out.println(incorrect);
        }
        else if (level==2)
        {
            for(int i=10;i<20;i++)
            {
                math_test_display(i);
            }
            System.out.println(correct);
            System.out.println(incorrect);
        }
        else
        {
            for(int i=20;i<30;i++)
            {
                math_test_display(i);
            }
            System.out.println(correct);
            System.out.println(incorrect);
        }
    }
    void math_test_display(int i)
    {
        if(c==0)
        {
            System.out.println("Please enter choice in form of Integer");
            c++;
        }
        if(Questions.question_maths[i]!=null) {
            System.out.println(Questions.question_maths[i]);
            for (int j = 0; j < 4; j++) {
                System.out.print(Questions.option_maths[i][j]);
                System.out.print("   ");
            }
            int choice = sc.nextInt();
            if (choice != 1 && choice != 2 && choice != 3 && choice != 4) {
                System.out.println("Invalid Choice");
                math_test_display(i);
            }
            else
            {
                if(Questions.answer_maths[i].equals(Questions.option_maths[i][choice-1]))
                {
                    correct++;
                }
                else
                {
                    incorrect++;
                }
            }
        }
    }
    void phy(int level)
    {
        if(level==1)
        {
            for(int i=0;i<10;i++)
            {
                phy_test_display(i);
            }
            System.out.println(correct);
            System.out.println(incorrect);
        }
        else if (level==2)
        {
            for(int i=10;i<20;i++)
            {
                phy_test_display(i);
            }
            System.out.println(correct);
            System.out.println(incorrect);
        }
        else
        {
            for(int i=20;i<30;i++)
            {
                phy_test_display(i);
            }
            System.out.println(correct);
            System.out.println(incorrect);
        }
    }
    void phy_test_display(int i)
    {
        if(c==0)
        {
            System.out.println("Please enter choice in form of Integer");
            c++;
        }
        if(Questions.question_physics[i]!=null) {
            System.out.println(Questions.question_physics[i]);
            for (int j = 0; j < 4; j++) {
                System.out.print(Questions.option_physics[i][j]);
                System.out.print("   ");
            }
            int choice = sc.nextInt();
            if (choice != 1 && choice != 2 && choice != 3 && choice != 4)
            {
                System.out.println("Invalid Choice");
                phy_test_display(i);
            }
            else
            {
                if(Questions.answer_physics[i].equals(Questions.option_physics[i][choice-1]))
                {
                    correct++;
                }
                else
                {
                    incorrect++;
                }
            }
        }
    }
}
class Test
{
    Scanner sc=new Scanner(System.in);
    int choice1=0;
    int  test()
    {
        System.out.println("Enter Difficulty Level");
        System.out.println("Enter 1 for Easy");
        System.out.println("Enter 2 for Medium");
        System.out.println("Enter 3 for Difficult");
        System.out.print("Enter Choice: ");
        choice1=sc.nextInt();
        if(choice1!=1 && choice1!=2 && choice1!=3)
        {
            System.out.println("Invalid Choice");
            test();
        }
        return choice1;
    }
}
class Student_leaderboard extends Student{
}
class Skill_Assessment_System
{
    public static void main(String[] args)
    {
        Scanner sc=new Scanner(System.in);
        Admin.Admin_Login adl= new Admin.Admin_Login();
        Student_Login ssl=new Student_Login();
        boolean flag=true;
        {
            System.out.println("========================================\n   Welcome to Skill Assessment System\n========================================");
        }
        while(flag)
        {
            System.out.print("Are you Student(S) or Admin(A)??(S/A):");
            char user=sc.next().charAt(0);
            if(user=='A' || user=='a')
            {
                System.out.print("Do you want to login(L) or Exit(E)? (L/E):");
                char choice=sc.next().charAt(0);
                if(choice=='e' || choice=='E')
                {
                    flag=false;
                }
                else if (choice=='L' || choice=='l')
                {
                    adl.Admin_login();
                }
                else{
                    System.out.println("Invalid Choice!!");
                }
            }
            else if (user=='S' || user=='s')
            {

                ssl.check_login();
            }
            else
            {
                System.out.println("Enter Valid User!!!");
            }
        }
    }
}
