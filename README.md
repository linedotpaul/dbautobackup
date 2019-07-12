# DB Autobackup via PHP

Automatically backs up your databases via scheduled tasks or cron.

Able to limit or rotate backups so that older backups are deleted.

## Installation

Download the source code. Depending on your platform, you either use the batch file `autobackup.bat` or the bash srcipt `autobackup.sh`. Copy the files to anywhere you like.

## Configuration

A sample config.php is given in the name of `config.sample.php`. copy it as `config.php` on the same directory. Edit `config.php` to configure the following:

* `backup_dir` - the location where you want to save your backup files.
* `keep_files` - the number of backup files to keep.
* `compression` - (Linux only) - allows backup compression by piping contents to compression tools like `gzip`, `bzip2`, etc.
* `db_host` - the host name where the database is running.
* `protocol` - defaults to empty string, options include `tcp`, `socket`, etc.
* `db_names` - an array of database names you want to backup. Make sure your user has access to use mysqldump to these databases.

__IMPORTANT__: Make sure to create first the directories where you want to save all your backup files for each database. For example:

If your backup dir is `D:/backup` and one of your database name is `market`, make sure you create first `D:/backup/market`. This applies to all databases you want to include.

## Database User and Password

These are stored in the .sqlcnf file to prevent the details being sent over the CLI.

__SECURITY NOTE__: .sqlcnf needs to be uploaded with very restricted file permissions on your server so that no-one else can access it. I suggest 6-0-0 or equivalent.

## Scheduling 

When scheduling the backup task, choose either `autobackup.sh` or `autobackup.bat` depending on your platform. For Linux, you can add the task via cron by adding this on your crontab. 

    0 0 * * *   /home/user/path/to/script/autobackup.sh

That effectively schedules backup every midnight.

Enjoy :D
