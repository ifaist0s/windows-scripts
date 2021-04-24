# windows-scripts
Scripts and utilities for the Windows OS command line

## 1. SQLBackup.CMD
This is a script that I use to automate:
1. Backup of Microsoft SQL Database(s)
2. Compress the backup file (using open source 7-Zip)
3. Copy/Move the backup file to SMB Share or elsewhere

### Script Dependencies
Some files are needed for the script to work
* The 7za.exe command line executable from the open source project [7-Zip](https://www.7-zip.org/).
* The [sqlcmd.exe](https://docs.microsoft.com/en-us/sql/tools/sqlcmd-utility?view=sql-server-ver15) command line executable that is installed along with Microsoft SQL Server.
* The Windows Management Instrumentation (WMI) Command-Line Utility ([Wmic.exe](https://docs.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page?redirectedfrom=MSDN)) that comes preinstalled in Windows 2000 and in newer OSes.

### Script Logic
The main FOR loop iterates through each item of the array (variables with SQL Server/DBs names) and does 4 jobs
1. Backup database (with or without transaction log)
2. Compress database (with or without transaction log)
3. Copy compressed backup file to another location
4. Clean-Up backup files older than X days (not implemented yes)
