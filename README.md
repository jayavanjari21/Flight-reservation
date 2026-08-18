##**Flight Reservation Application**##

#**Project Overview**
The Flight Reservation Application is a web-based application designed to manage flight reservation operations.
#The application consists of:
1.Frontend
2.Java Backend
3.MySQL Database
#The project is built using Java and Maven for the backend, a frontend application using Node.js/npm, and MySQL for database management.

#**Architecture**
User
 |
 v
Frontend
 |
 v
Java Backend
 |
 v
MySQL Database

#**Technologies Used**
Backend: Java
Build Tool: Maven
Frontend: Node.js / npm
Database: MySQL
Web Server: Aws
Operating System: Linux
Version Control: Git and GitHub

#**Project Structure**
Flight-reservation/
│
├── FlightReservationApplication/   # Java Backend
├── frontend/                       # Frontend Application
├── sql.txt                         # Database setup
├── BuildCommands.txt               # Build instructions
└── README.md                       # Project documentation

---

#**Steps to deploy Application**
1. Clone this repository
```shell
git clone https://github.com/jayavanjari21/Flight-reservation.git
cd Flight-reservation
```

2. Install Mysql Server and create database
```shell
apt update -y
apt install mysql-server -y
mysql_secure_installation
mysql -uroot -p
>> create user linux identified by "Redhat";
>> grant all privileges on *.* to linux;
>> flush privileges;
>> create flightdb;
>> exit
```

3. Deploy Backend
```shell
cd Flight-reservation
cd FlightReservationApplication
apt install openjdk-17-jdk -y
apt install maven -y
export DATASOURCE_URL="jdbc:mysql://localhost:3306/flightdb"
export DATASOURCE_USER="linux"
export DATASOURCE_PASSWORD="Redhat"
export FRONTEND_URL="http://localhost:80"
mvn clean package
java -jar target/flight*.jar
```

4. Deploy Frontend (open new tab)
```shell
cd Flight-reservation
cd frontend
apt install nodejs npm -y
export VITE_API_URL=http://localhost:8080
npm install
npm run build
apt install apache2 -y
cp dist/* /var/www/html/
systemctl start apache2
```
