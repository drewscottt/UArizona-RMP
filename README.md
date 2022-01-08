## Description
The included notebook contains the steps I took in the ETL process for my final project in ISTA 322 (Data Engineering) at University of Arizona in Fall 2021. The project's goal was to merge two datasets (a public salary dataset of UArizona employees and the RateMyProfessor information for all UArizona professors) and load them into a database to allow for easy access. A few sample queries have been included at the end of the notebook to show what sorts of queries can be asked.

## Usage
Connecting to the database:
```python
import mysql.connector as mysql
conn = mysql.connect(host="54.184.86.6", database="rmp_ista", user="select_rmp", password="select_rmp")
```
Tables:
<pre>
* Professor
+---------------------+--------------+------+-----+---------+-------+  
| Field               | Type         | Null | Key | Default | Extra |  
+---------------------+--------------+------+-----+---------+-------+  
| FirstName           | varchar(50)  | YES  |     | NULL    |       |  
| LastName            | varchar(50)  | YES  |     | NULL    |       |  
| ProfID              | int          | NO   | PRI | NULL    |       |  
| NumRatings          | int          | YES  |     | NULL    |       |  
| AverageRating       | double       | YES  |     | NULL    |       |  
| Title               | varchar(100) | YES  |     | NULL    |       |  
| AcutalSalary        | int          | YES  |     | NULL    |       |  
| FTESalary           | int          | YES  |     | NULL    |       |  
| Department          | varchar(100) | YES  |     | NULL    |       |  
| InferredGender      | varchar(10)  | YES  |     | NULL    |       |  
| EthnicityConfidence | double       | YES  |     | NULL    |       |  
| InferredEthnicity   | varchar(10)  | YES  |     | NULL    |       |  
+---------------------+--------------+------+-----+---------+-------+    

* Review
+---------------+---------------+------+-----+---------+-------+  
| Field         | Type          | Null | Key | Default | Extra |  
+---------------+---------------+------+-----+---------+-------+  
| ReviewID      | int           | NO   | PRI | NULL    |       |  
| ClarityRating | double        | YES  |     | NULL    |       |  
| CourseID      | varchar(20)   | YES  |     | NULL    |       |  
| Comment       | varchar(5000) | YES  |     | NULL    |       |  
| ReviewDate    | date          | YES  |     | NULL    |       |  
| EasyRating    | double        | YES  |     | NULL    |       |  
| HelpfulRating | double        | YES  |     | NULL    |       |  
| OverallRating | double        | YES  |     | NULL    |       |  
| CourseGrade   | varchar(20)   | YES  |     | NULL    |       |  
| ProfID        | int           | YES  |     | NULL    |       |  
| CoursePercent | double        | YES  |     | NULL    |       |  
+---------------+---------------+------+-----+---------+-------+  

* Department
+-----------------+--------------+------+-----+---------+-------+  
| Field           | Type         | Null | Key | Default | Extra |  
+-----------------+--------------+------+-----+---------+-------+  
| Department      | varchar(100) | NO   | PRI | NULL    |       |  
| NumProfessors   | int          | YES  |     | NULL    |       |  
| AvgRating       | double       | YES  |     | NULL    |       |  
| AvgFTESalary    | double       | YES  |     | NULL    |       |  
| TotalProfPay    | int          | YES  |     | NULL    |       |  
| Percentwhite    | double       | YES  |     | NULL    |       |  
| Percentblack    | double       | YES  |     | NULL    |       |  
| Percentapi      | double       | YES  |     | NULL    |       |  
| Percentaian     | double       | YES  |     | NULL    |       |  
| Percent2prace   | double       | YES  |     | NULL    |       |  
| Percenthispanic | double       | YES  |     | NULL    |       |  
| Percentnonwhite | double       | YES  |     | NULL    |       |  
+-----------------+--------------+------+-----+---------+-------+  

* Course
+----------------+--------------+------+-----+---------+-------+  
| Field          | Type         | Null | Key | Default | Extra |  
+----------------+--------------+------+-----+---------+-------+  
| CourseID       | varchar(20)  | NO   | PRI | NULL    |       |  
| AvgEasy        | double       | YES  |     | NULL    |       |  
| AvgHelpful     | double       | YES  |     | NULL    |       |  
| AvgClarity     | double       | YES  |     | NULL    |       |  
| AvgOverall     | double       | YES  |     | NULL    |       |  
| MostCommonProf | int          | YES  |     | NULL    |       |  
| AvgGrade       | double       | YES  |     | NULL    |       |  
| NumRatings     | int          | YES  |     | NULL    |       |  
| ProfID         | int          | YES  |     | NULL    |       |  
| Department     | varchar(100) | YES  |     | NULL    |       |  
+----------------+--------------+------+-----+---------+-------+  
</pre>
