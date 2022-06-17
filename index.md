## DAT602 Milestone Reviews

### Milestone One Review

For this milestone I started with a project brief and storyboarding / screen design. I used storyboardthat a website that is very handy for storyboarding. Although it means my assets, I used from stroyboardthat are not representative of the final GUI it is a small price to pay to use a very easy storyboarding website.

My screens I designed in ADOBEXD and I referenced how windows forms looked in the tutorial in another class to reference as I drew up some basic wireframes of my screens.
I installed MySQL workbench and worked on my Entity Relationship Diagram or in this case my Enhanced Entity Relationship (EER). Which means it is a more up to date version of the ERD model. It was very convenient that the EER diagram was inside the schema of MySQL workbench so I could create my Schema (think database) then create and save my EER and my DDL SQL scripts as a single file. It made it very easy to complete my work. EER is in my schema file in the model overview tab named EER (MySQL :: MySQL Workbench Manual :: 9.1.1.4 The Physical Schemas Panel, n.d.).

I had some trouble with my DDL as I didn’t use ON UPDATE CASCADE, ON DELETE CASCADE; (MySQL ON DELETE CASCADE: Deleting Data from Related Tables Automatically, n.d.) with my foreign keys at first. I also did not create my foreign key relationships the correct way at first and needed to correct both of these mistakes. When I got to the delete SQL part of the assessment, I found I could not delete records because I did not cascade my foreign keys. I had playerIsAdmin as a unique field before I realised this mistake, I could only have one user and one admin in the tables. I also corrected this mistake by updating my DDL SQL which is the script file in the SQL script file attached to my schema file.

I practiced SQL in class, but I had to reference delete syntax from (‘MySQL DELETE - Deleting Data from a Table’, n.d.). The procedure I sourced from the class documents text file Procedural TSQL starter. 
I couldn’t update the playerScore field in this example because the plan is to have the item value on pickup be added to the playerScore and I did not think it was necessary to produce a procedure to insert a value into it when null is a valid starting score as all it means is nothing.

My CRUD (What Is CRUD? | Codecademy, n.d.) or Insert Select Update Delete script is in a file called script1 in the SQL scripts area in the schema file I attached to the moodle assessment. As mentioned, before I had a little trouble with it but with class references and some other syntax searches, I managed to use insert, select, update on every table on all rows and delete on the second row in all tables.

After I succeeded in my CRUD actions, I then set about analysing them with my CRUD table in the report. As it is a database, I found I was reading and updating a lot more than deleting data. Which makes sense because you want to store data and very rarely delete it.


#### References

MySQL DELETE - Deleting Data from a Table. (n.d.). MySQL Tutorial. Retrieved 18 March 2022, from https://www.mysqltutorial.org/mysql-delete-statement.aspx

MySQL :: MySQL Workbench Manual: 9.1.1.4 The Physical Schemas Panel. (n.d.). Retrieved 18 March 2022, from https://dev.mysql.com/doc/workbench/en/wb-view-overview-physical-schemas.html

MySQL ON DELETE CASCADE: Deleting Data from Related Tables Automatically. (n.d.). Retrieved 18 March 2022, from https://www.mysqltutorial.org/mysql-on-delete-cascade/

What is CRUD? | Codecademy. (n.d.). Retrieved 18 March 2022, from https://www.codecademy.com/article/what-is-crud


### Milestone Two Review

For this milestone I created SQL procedures (storedProcedures.sql file) related to the game I outlined in milestone one. The area I focused on was the user login, registration, and administrator functions / creation. I got them working in sql then created a dataaccessobject in C# to connect the test cases to the database with intermediates.

```
private static MySqlConnection _mySqlConnection = null;
        public static MySqlConnection mySqlConnection
        {
            get
            {
                if (_mySqlConnection == null)
                {
                    _mySqlConnection = new MySqlConnection(connectionString);
                }

                return _mySqlConnection;

            }
        }
```
Connection function (omitted the string) above is how the C# connected to the database.

```
public string RegisterPlayer(string pUserName, string pPassword)
        {

            List<MySqlParameter> p = new List<MySqlParameter>();
            var aP = new MySqlParameter("@UserName", MySqlDbType.VarChar, 45);
            aP.Value = pUserName;
            p.Add(aP);

            var bP = new MySqlParameter("@Password", MySqlDbType.VarChar, 45);
            bP.Value = pPassword;
            p.Add(bP);

            var aDataSet = MySqlHelper.ExecuteDataset(DataAccessObject.mySqlConnection, "CALL registerPlayer(@UserName, @Password)", p.ToArray());

            // expecting one table with one row
            return (aDataSet.Tables[0].Rows[0])["MESSAGE"].ToString();

        }
```
This is the function required to call the SQL function into C#. It is creating two arguments which line up with the SQL procedure then the executedataset is called which we then use the connection string to call the procedure using the dataset to help parse the data.

```
   static void CheckUsernameAndPassword(string username, string password, DataAccessObject _dao)
            {
                Console.WriteLine("\nTesting checkUsers");
                Console.WriteLine("===============================================");
                Console.WriteLine($"{username} {password}");

                if (_dao.CheckUsernameAndPassword(username, password) == ("Login succesful"))
                {
                    Console.WriteLine($"User {username} logged in successfully");
                }
                else
                {
                    Console.WriteLine("Incorrect login details");
                }
                Console.WriteLine("----------------------------------------------");
            }
            
                 RegisterPlayer("bobc", "P@ssword1", _dao);
```
Writing the function to test if the SQL procedure is being called correctly by the previous function. It is called with the arguments set out in the C# and SQL functions that has the shortened form of dataaccessobject as an argument so it connects to the SQL connection in the object.

The last code snippet is the console app output that happens when you run dat602CLR portion of the application I have submitted. It runs through all the called methods and outputs the results. I have verified that they all work.

I have written up all the functions in SQL and C# I have created in the Milestone 2 portion of the Dat602 Project Final Hand In.

Also within the milestone two portion of the Final Hand In is the ACID Transactions write up which is the Atomicity, Consistency, Isolation, Durability principles that make up transactions (Database Concepts, n.d.). 

Transactions are most useful when procedures touch multiple tables to make sure that no bad data is passed when doing complicated inserts and updates or deletes of data across multiple tables. If a procedure interacts/touches multiple tables it might be better to make it a transaction. Transactions are also ACID by default if you use the basic transaction syntax (What Does ACID Mean in Database Systems?, n.d.).

#### References

What are ACID Transactions? (n.d.). Databricks. Retrieved 20 May 2022, from https://databricks.com/glossary/acid-transactions

What does ACID mean in Database Systems? (n.d.). Retrieved 20 May 2022, from https://database.guide/what-is-acid-in-databases/

### Milestone Three Review

For milestone three I imported the methods with some tweaks from the C# dat602CLR dataaccessobject into databaseaccessobject for the connection string and objects calling the procedures from the database. I also created forms with fields, labels and buttons corresponding to the arguments/data that needed to be passed, then passing them via buttons.

The dataaccessobjects classes stayed the same but the front end functions had to be rebuilt. I choose continue having lightweight methods in the forms as well as ways to open forms after the right buttons were pressed.

I then added a write up to the report about my GUI forms and what they do with text fields and buttons explained how they work. 

I implemented the link between the database and the C# intermediary functions/classes then the front end form C# code that writes and reads from the database.

I then finalised the report from milestone one, two and three updating what had changed in the milestones due to milestone three being added or improvements being made.
