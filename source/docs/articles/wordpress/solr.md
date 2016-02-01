---
title: Enabling Solr for WordPress
description: Detailed information on using Apache Solr with WordPress.
category:
    - wordpress
    - developing
keywords: apche, apache solr, index, indexing, searching, index and search, indexing and searching, solr, how to enable solr, enable solr, solr api, indexserver solr, solr indexserver, solr api, enable solr search, apachesolr, apache solor search module, solr modules, configure solr,
---
[Apache Solr](/docs/articles/sites/apache-solr) is a system for indexing and searching site content. First, you will need to add the index server to your site. From your Dashboard, go to **Settings** > **Add Ons** > **Apache Solr Index Server: Add**.

This will provision Apache Solr containers for every environment. You are now ready to begin integrating with WordPress.

## Solr Search for WordPress
Pantheon supports and maintains [Solr Search for WordPress](https://wordpress.org/plugins/solr-power/).  This plugin replaces the default search mechanism within WordPress while preserving the familiar integration methods within themes and widgets.


## Install and Configure the Plugin
1. [Set the connection mode to SFTP](/docs/articles/sites/code/developing-directly-with-sftp-mode) for the Dev or Multidev environment via the Pantheon Dashboard or with [Terminus](/docs/articles/local/cli/):
 ```bash
 terminus site set-connection-mode --site=<site> --env=dev --mode=sftp
 ```

2. Install and activate the [Solr Search for WordPress](https://wordpress.org/plugins/solr-power/) plugin on the Dev environment using the WordPress dashboard or with Terminus:
 ```bash
 terminus wp 'plugin install --activate solr-power' --site=<site> --env=dev
 ```
 Upon activation, the plugin will index your site automatically using the default indexing options.

3. From the WordPress Dashboard, navigate to **Settings** > **Solr Options**. You should see the **Info** tab which shows your site's Solr server details.

4. Select the **Indexing** tab to customize your indexing options with Solr. For example, Network Administrators on a given WordPress Site Network can select the **Index All Sites** option to extend Solr to all subsites. 

5. Use the **Actions** tab to perform the following Solr tasks:
 - Check Server Settings
 - Optimze Index
 - Delete All
 - Repost schema.xml
 - Load All Post(s)
 - Load All Page(s)
 - Load All Attachment(s)
 <div class="alert alert-info">
 <h4>Note</h4>
 To use a custom <code>schema.xml</code>, upload it to the <code>/wp-content/uploads/solr-for-wordpress-on-pantheon/</code> directory.
 </div>
6. Use the **Query** tab to search for words or phrases to validate Solr's indexing configuration.
