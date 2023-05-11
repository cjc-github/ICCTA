# ICCTA

This is a specific installation and implementation of ICCTA

## step 1: install sql

```
sudo apt-cache search mysql-server
sudo apt install mysql-server-5.7
```

## Step 2:create user and database

```
mysql -uroot -prootroot
create user li@localhost identified by 'changeme';
grant all privileges on cc.* to li@localhost;
exit
```

### Step3:Config the mysql

```
mysql -uli -pchangeme -e 'create database cc';
mysql -uli -pchangeme cc < res/schema;
```

Then,you can show the sql information

```
mysql -uli -pchangeme
show databases;
use cc;
show tables;
```

# Run ICCTA

You can using ICCTA or FlowDroid without IC3 to achieve ICC.

## ICCTA

```
java -jar iccta.jar apk_name ../platforms/
```


## FlowDroid without ICC model

```
java -jar ic3.jar -a ActivityCommunication2.apk -cp ../../android-platforms/ -db cc.properties -protobuf Icc_result_folder

The Icc_result_folder folder must be created in advance.you can use `mkdir Icc_result_folder` to achieve it.
```

Then, using option -im to enhance Flowdroid to achieve ICC detection.

```
java -jar flowdroid-2.10.jar -a apk -p ./platforms/ -s SourceAndSinks.txt -im Icc_result_folder/***.txt
```

Finish!!!
