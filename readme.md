#Export From Expression Engine to WordPress

Refers to Expression Engine 1.6.7

Create a working local copy of the EE site:

1. Download database
2. Create an empty target database locally
3. Backup local DBs ```mysqldump -u username -p --all-databases > all_localhost_databases.sql```
3. Import the Database: ```mysql -u username -p target_db < ~/Downloads/download.sql```
2. Download files and place EE site in the document root directory e.g. /var/www/ee-site
3. Amend /var/www/ee-site/app/config.php to reflect database settings
4. This may allow access to the admin area via localhost/ee-site/app/index.php

In Expression Engine admin area:

Templates >> Create a New Template Group (in this case, called "Exports").

Choose Group (select "Exports") >> New Template

Create a new template called "data.xml" and set template type to "xml".

Paste contents of ```data.xml``` here.

Amend lines 51 & 52 to reflect the correct EE field names:

~~~
<content:encoded><![CDATA[{if news-body}{news-body}{/if}]]></content:encoded>
<excerpt:encoded><![CDATA[{if news-summary}{news-summary}{/if}]]></excerpt:encoded>
~~~

##Find Correct EE Fields
Templates >> Choose Group >> Click relevant template name

You will see the relevant fields in the template content.

##Resources
The data.xml code was taken from this tutorial:
http://www.phpdevtips.com/2011/08/how-to-import-an-expressionengine-blog-into-wordpress/

http://www.hopstudios.com/blog/exporting_from_expressionengine_into_wordpress#.VCpWZHVdUYP

http://www.farces.com/wikis/naked-server/wordpress/ee-migration/

http://kodegeek.wordpress.com/2009/12/02/export-import-expressionengine-to-wordpress/

http://www.bettnet.com/moving-expression-engine-1-wordpress/
