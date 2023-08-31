# COSC 304 - Introduction to Database Systems<br>Lab 2: Creating Tables using SQL and MySQL

This lab practices creating tables using SQL DDL on a MySQL database.

**Make sure your computer is setup to run Docker by following these [setup instructions](../setup).**

### Step #1: Setup MySQL Docker Container

 - Create a directory `cosc304_lab2`.
 - Download the `docker-compose.yml` file into the `cosc304_lab2` directory. 
 - Create a folder `ddl` in `cosc304_lab2` directory. Download the contents of the `ddl` folder into the `cosc304_lab2\ddl` folder.
 - Open a command shell either directly on your machine or using VSCode. Make sure your current directory is `cosc304_lab2`.
 - Run the command `docker-compose up -d`
 - If everything is successful, the MySQL database will start on port 3306. If there is a port conflict, change the port to 3307 in the `docker-compose.yml` file.
 - Your database is `mydb`. There are other databases also created such as `workson` and `university`.

## Step #2: Access MySQL using Command Interface

MySQL commands can be running using the command line within the Docker container. Run the command:

```
docker exec -it cosc304-mysql bash
```

This will start a command line session. Connect to MySQL using:

```
mysql -u root -p
```
OR
```
mysql -u testuser -p
```

The password is given in the `docker-compose.yml` file (which you are **encouraged to change**). Note that all commands are terminated with a semi-colon (`;`). Some useful commands are:

| Function  | Command |
| ------------- | ------------- |
| Listing all databases	  | `show databases;`  |
| Use database `dbname`  | `use dbname;`  |
| List all tables  | `show tables;`  |

![Connecting using MySQL Command Line](img/commandline.png)

### Step #2: Accessing MySQL using SQuirreL SQL

[SQuirreL](http://squirrel-sql.sourceforge.net) is an open source graphical query tool capable of querying any JDBC-accessible database including Oracle, MySQL, and SQL Server.

[Download and install MySQL JDBC driver](mysql-connector-java-8.0.27.jar) and put it in the SQuirreL `lib` folder.

Start up SQuirreL.  Register our MySQL server with the information: 

<pre>
Name: MySQL
Login name: root
Password: (see docker-compose.yml file)
Host name: localhost
Port: (leave blank for default)
Database: mydb
</pre>

<img src="img/squirrel-mysql.png" width="400" alt="MySQL Connection Setup in SQuirreL">

### Step #3: Example SQL DDL

The university database should already be loaded. If you have any issues, using SQuirreL, create the tables and load the data for the [university database using this DDL script](ddl/university_MySQL_DDL.sql).  

### Step #4: Practice SQL DDL

As practice, here are some changes to make to the existing the database.  You can answer the questions in groups.

#### CREATE TABLE Command

1. Create a new table called `dept` with attributes `deptId INTEGER`, `deptName VARCHAR(40)`, and `deptLocation VARCHAR(50)`.

2. Create a new table called `courseDept` with attributes `deptId INTEGER` and `cname VARCHAR(40)`.

#### INSERT Command

<ol>
<li>Insert these records into <tt>dept</tt>:
<pre>
deptId,deptName,deptLocation
11,'Law', 'Arts 333'
12,'Fine Arts', 'Arts 333'
20,'Computer Science', 'Arts 333'
33,'Mathematics', 'Science 234'
68,'Engineering', 'SSC 100'
</pre></li>

<li>Add these three records into <tt>faculty</tt>:
<pre>
fid, fname, deptId
'111111111','Yves Lucet',20
'222222222','Yong Gao',20
'333333333','Ramon Lawrence',20
</pre></li>
</ol>

#### DELETE Command

<ol>
<li>Delete the student with number = <tt>'318548912'</tt>.</li>
</ol>

#### UPDATE Command

<ol>
<li>Change the name of student <tt>'Steven Green'</tt> to <tt>'Steven Yellow'</tt>.  Update his age to be <tt>20</tt> as well.</li>
</ol>

#### ALTER TABLE Command

<ol>
<li>Modify the faculty table so that the <tt>deptId</tt> is a foreign key to the <tt>dept</tt> table.</li>
</ol>

#### Various Commands

<ol>
<li>Add tuples to the <tt>courseDept</tt> relation.  This relation gives what departments teach what courses.  Populate the data based on the department number of the faculty member currently teaching the course.  If no one is currently teaching the course, the course should be given to department <tt>20</tt>.</li>

<li>Change the name of the course <tt>'Database Systems'</tt> to <tt>'Introduction to Database Systems'</tt>.  Update all affected records.</li>

<li>Change the <tt>course</tt> table to include an integer field called <tt>studentCount</tt> that counts all the students currently enrolled in the course.  Populate this field for all courses based on current enrollment information.</li>

<li>Remove student with id = <tt>'115987938'</tt> from the database and all courses the student is enrolled in.  Make sure to modify the <tt>studentCount</tt> field created in the previous section as appropriate.</li>


<li><B>Challenge: Do you have an SQL DDL that you think others cannot answer?  If so, let the TA know.</B></li>

</ol>

**Answers:**  <a href="labAnswers_DDL.txt">Download the answer script file</a>.</p>

# [Lab 2 - SQL Lab Assignment](assign/)

