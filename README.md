# SOAP and REST Solutions
Go to the directory for each service (REST and SOAP) and compile the files with the following command on your machine:
```bash
mvn clean package
```
Then, move the `.jar` files to the Azure VM
```bash
scp /path/to/file username@a:/path/to/destination
```
*An example:*
```bash
scp /home/kjetteren/Documents/dsgt2-rest/dsgt-rest/target/food-rest-service-0.0.1-SNAPSHOT.jar azureuser@dsgt.eastus.cloudapp.azure.com:~/REST
scp /home/kjetteren/Documents/dsgt2-soap/dsgt-soap/target/SpringSOAP-0.0.1-SNAPSHOT.jar azureuser@dsgt.eastus.cloudapp.azure.com:~/SOAP
```
To run the files on the Azure VM ssh into the VM and run with the following command:
```bash
java -jar /path/to/file
```
*An example:*
```bash
java -jar ~/REST/food-rest-service-0.0.1-SNAPSHOT.jar
java -jar ~/SOAP/SpringSOAP-0.0.1-SNAPSHOT.jar
```
To test that it is running, run one of the commands using the `.xml` file or run a command stored in `.sh` files. *An example (ran from the folders where the requests are stored):*
```bash
curl -X POST dsgt.eastus.cloudapp.azure.com:8080/rest/meals -H 'Content-type:application/json' -d @new-meal.json -v
curl --header "content-type: text/xml" -d @request.xml http://dsgt.eastus.cloudapp.azure.com@:8080/ws
```
