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

