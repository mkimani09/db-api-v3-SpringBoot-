Order of Starting Jar files
Eureka: 7600
Load-Balancer:8585
App: 7601

Open ports
firewall-cmd --zone=public --permanent --add-port=6600/tcp
firewall-cmd --zone=public --permanent --add-port=8585/tcp
firewall-cmd --zone=public --permanent --add-port=6601/tcp
firewall-cmd --reload






ps -ef | grep eureka-service-discovery-v1.jar

ps -ef | grep db-api-load-balancer-v2.jar


ps -ef | grep db-api-v3-v1.jar



WIthout Tmp /Faulu

nohup java -jar eureka-service-discovery-v1.jar&
nohup java -jar db-api-load-balancer-v2.jar&
nohup java -jar db-api-v3-v1.jar&

Without writing to nohup
nohup java -jar db-api-v3-v1.jar >/dev/null &

Start without nohup logging
nohup java -jar db-api-v3-v1.jar >/dev/null &

--New instance
nohup java -Xmx2048M -Dserver.port=8890 -jar db-api-v3-v1.jar >/dev/null &


Check Dashboard
http://172.16.4.138:6600/dashboard


DB-Api end points
1) View All procedures
http://172.16.4.138:8585/ebankdb/db-api/fetch-stored-procedures

2)Exec Procedures

http://172.16.4.138:8585/ebankdb/db-api/execute-stored-procedure

3) Exec  SQL STATEMENT
POST http://172.16.4.138:8585/ebankdb/execute-operations


telnet 10.229.119.221 8585
Refresh Objects
curl -X POST http://172.16.4.138:8585/ebankdb/db-api/fetch-stored-procedures
curl -X POST http://172.16.4.138:8585/ebankdb/db-api/fetch-database-operations
curl -X POST http://172.16.4.138:6601/db-api/fetch-database-operations

curl -X POST http://10.1.24.31:8585/ebankdb/db-api/fetch-database-operations

check ports
ss -nulpt
