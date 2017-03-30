# AWS-EB-EFS
AWS Elastic Beanstalk and EFS notes

PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'ebdb.semaphore' doesn't exist: SELECT expire, value FROM {semaphore} WHERE name = :name; Array ( [:name] => variable_init ) in lock_may_be_available() (line 167 of /var/app/current/includes/lock.inc).

Uncaught exception thrown in shutdown function.
PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table &#039;ebdb.semaphore&#039; doesn&#039;t exist: DELETE FROM {semaphore} WHERE (value = :db_condition_placeholder_0) ; Array ( [:db_condition_placeholder_0] =&gt; 13138921658dc7972039825.10467903 ) in lock_release_all() (line 269 of /var/app/current/includes/lock.inc).


Installation tasks
Choose profile
Choose language
Verify requirements
Set up database
Install profile
Configure site
Finished
Sorry, the profile you have chosen cannot be loaded. 

Error: Call to undefined function field_attach_load() in DrupalDefaultEntityController->attachLoad() (line 354 of /var/app/current/includes/entity.inc).

After a lot of searching I found a solution, in that you need to incease the 'max_execution_time' and 'max_input_time' in the php.ini file. I used a value of 120 rather than the default 30. This allowed the database build to complete.

Troubleshooting
Logs

Logs of the execution of .ebextension/*.config files are found in /var/log/cfn-init.log.

You should see something like

[DEBUG] Installing/updating [u'php55-pecl-apc'] via yum
[INFO] Yum installed [u'php55-pecl-apc']
