# FlightReservationApplication
flight booking web application

Steps to deploy Application
Clone this repository
git clone https://github.com/shubhamkalsait/Flight-reservation.git

Install Mysql Server and create database
apt update -y
apt install mysql-server -y
mysql_secure_installation
mysql -uroot -p
>> create user linux identified by "Redhat";
>> grant all privileges on *.* to linux;
>> flush privileges;
>> create flightdb;
>> exit
>> 
Deploy Backend
cd Flight-reservation
cd FlightReservationSystem
apt install openjdk-17-jdk -y
apt install maven -y
export DATASOURCE_URL="jdbc:mysql://localhost:3306/flightdb"
export DATASOURCE_USER="linux"
export DATASOURCE_PASSWORD="Redhat"
export FRONTEND_URL="http://localhost:80"
mvn clean package
java -jar target/flight*.jar

Deploy Frontend (open new tab)
cd Flight-reservation
cd frontend
apt install nodejs npm -y
export VITE_API_URL=http://localhost:8080
npm install
npm run build
apt install apache2 -y
cp dist/* /var/www/html/
systemctl start apache2
