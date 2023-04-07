**Task 0
Open a new terminal by clicking on the menu bar and selecting Terminal->New Terminal:**

Download the template file backup.sh by running the command below:

`wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-LX0117EN-SkillsNetwork/labs/Final%20Project/backup.sh`

Open the file in the IDE by clicking File->Open as seen below:

![image](https://user-images.githubusercontent.com/121275064/230525841-fb79b3bf-5a19-4971-a355-59f930da0e83.png)

and then click on the file, which should have been downloaded in the project directory:

![image](https://user-images.githubusercontent.com/121275064/230525882-81368347-2d18-4a85-8513-1ba85dc73e86.png)

**About the template script, backup.sh
You will notice the template script contains comments (lines starting with the # symbol). Do not delete these.
The ones that look like “# [TASK {number}]“ will be used by your grader:**

![image](https://user-images.githubusercontent.com/121275064/230526087-27aaf205-ae2a-4fb5-8775-ba490ea3592f.png)

**Also, please do not modify any existing code above # [TASK 1] in the script.**

**Task 1
Navigate to # [TASK 1] in the code.**

Set two variables equal to the values of the first and second command line arguments, as follows:

Set targetDirectory to the first command line argument
Set destinationDirectory to the second command line argument
(This task is meant to help with code readability)

<img width="148" alt="T1" src="https://user-images.githubusercontent.com/121275064/230526127-bac7041e-33c9-472b-a4c2-97e43cd268dc.png">

**Task 2
Display the values of the two command line arguments in the terminal.**

<img width="215" alt="T2" src="https://user-images.githubusercontent.com/121275064/230526193-bfbd023a-63c7-4c10-8f52-28ee0bab524c.png">

**Task 3
Define a variable called currentTS as the current timestamp, expressed in seconds.**

<img width="137" alt="T3" src="https://user-images.githubusercontent.com/121275064/230526204-e0d01db3-2916-4db3-ab92-02529d4e75ec.png">

**Task 4
Define a variable called backupFileName to store the name of the archived and compressed backup file that the script will create.
The variable backupFileName should have the value "backup-[$currentTS].tar.gz"
For example, if currentTS has the value 1634571345, then backupFileName should have the value backup-1634571345.tar.gz.**

<img width="247" alt="T4" src="https://user-images.githubusercontent.com/121275064/230526648-f066bc4e-80b0-4e7e-b880-a450b6040582.png">

**Task 5
Define a variable called origAbsPath with the absolute path of the current directory as the variable’s value.**

<img width="122" alt="T5" src="https://user-images.githubusercontent.com/121275064/230526670-e084f7c9-e924-447a-b8d2-0ad119f085f8.png">

**Task 6
Define a variable called destAbsPath with value equal to the absolute path of the destination directory.**

<img width="157" alt="T6" src="https://user-images.githubusercontent.com/121275064/230526674-0d4f3788-1999-49c1-b3f0-ecbfe7b24f2a.png">

**Task 7
Change directories from the current working directory to the target directory targetDirectory.**

<img width="122" alt="T7" src="https://user-images.githubusercontent.com/121275064/230526692-8160f1c8-3b19-4c2b-b85c-48be93dd3f86.png">

**Task 8
You need to find files that have been updated within the past 24 hours.
This means you need to find all files who’s last modified date was 24 hours ago or less.**

To do make this easier:

Define a numerical variable called yesterdayTS as the timestamp (in seconds) 24 hours prior to the current timestamp, currentTS

<img width="122" alt="T7" src="https://user-images.githubusercontent.com/121275064/230526718-5643635a-7c30-4306-8d9d-b3508d8e4732.png">

**Task 9
Within the $() expression inside the for loop, write a command that will return all files and directories in the current folder.**

<img width="208" alt="T9" src="https://user-images.githubusercontent.com/121275064/230526789-2e685a22-c45d-4d57-afd0-204438f39dc2.png">

**Task 10
Inside the for loop, you want to check whether the $file was modified within the last 24 hours.
To get the last-modified date of a file in seconds, use date -r $file +%s
Then compare the value to yesterdayTS
Idea: if [[ $file_last_modified_date > $yesterdayTS ]] then the file was updated within the last 24 hours!
Since much of this wasn’t covered in the course, for this task you may copy the code below and paste it into the double round brackets (()):
1
`date -r $file +%s` > $yesterdayTS**

![T1011](https://user-images.githubusercontent.com/121275064/230526799-da71ca06-eca6-48a5-b2a3-a8579c546152.PNG)

**Task 11
In the if-then statement, add the $file that was updated in the past 24-hours to the toBackup array.
Since much of this wasn’t covered in the course, you may copy the code below and place after the then statement for this task:
1
toBackup+=($file)**

![T1011](https://user-images.githubusercontent.com/121275064/230526808-ab95ebe1-f814-443e-a8b0-fcbb0a53c025.PNG)

**Task 12
After the for loop, compress and archive the files, using the $toBackup array of filenames, to a file with the name backupFileName.**

![T12](https://user-images.githubusercontent.com/121275064/230526851-ec20e190-4512-4c76-978d-c271726a7392.PNG)

**Task 13
Now the file $backupFileName is created in the current working directory.**

![T13](https://user-images.githubusercontent.com/121275064/230526859-29dc4d83-aee5-4f48-a8f6-5fa527747650.PNG)

Move the file backupFileName to the destination directory located at destAbsPath.
You are now done the coding portion of the lab!

Task 14
Open a new terminal by clicking on the menu bar and selecting Terminal->New Terminal

**Task 15
Save the file you’re working on (backup.sh) and make it executable.**

Verify the file is executable using the ls command with the -l option:

`ls -l backup.sh`

![T15](https://user-images.githubusercontent.com/121275064/230526938-11b6769c-d59b-4048-979d-27e0a942e61c.PNG)


**Task 16
Download the following zip file with the wget command:**

`wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-LX0117EN-SkillsNetwork/labs/Final%20Project/important-documents.zip`

Unzip the archive file:

`unzip -DDo important-documents.zip`

(-DDo to overwrite and not restore original modified date)

Update the file’s last modified date to now:

`touch important-documents/*`

Test your script using the following command:

`./backup.sh important-documents .`

This should have created a file called backup-[CURRENT_TIMESTAMP].tar.gz in your current directory

![16-backup-complete](https://user-images.githubusercontent.com/121275064/230527018-185a1b3e-f464-48f3-b1b7-968f8407c804.PNG)

**Task 17
Copy (don’t mv) the backup.sh script into the /usr/local/bin/ directory.**

Note: You may need to use sudo cp in order to create a file in /usr/local/bin/
Test the cronjob to see if the backup script is getting triggered by scheduling it for every 1 minute.


Please note that since the Theia Lab is a virtual environment, we need to explicitly start the cron service using the below command.

`sudo service cron start`

Once the cron service is started, please check in the directory (/home/project) if the tar files are getting created.

![17-crontab](https://user-images.githubusercontent.com/121275064/230527221-822bdece-0490-48f3-ad54-eaa61a0660c5.PNG)

If yes, then please stop the cron service using the below command, else it will continue to create tar files every minute.


`sudo service cron stop`

Using crontab, schedule your /usr/local/bin/backup.sh script to backup the important-documents folder every 24 hours to the directory (/home/project).

