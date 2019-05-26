# Entry Revisions Plugin
Entry Revisions plugin for EE5
# Requirements
- ExpressionEngine 5+
- PHP 5.5+
- MySQL 5+
# Instalation Guide
Unzip and upload "entry_revisions" into "system/user/addons/"
# Parameters
**channel [Optional]**: Name of the channel. You can use the pipe character ("|") to query by multiple channels.
```
{exp:entry_revisions channel="blogs|news"}
#####
{/exp:entry_revisions}
```
**author_id [Optional]**: The member id of the author of the entry or entry revisions.
```
{exp:entry_revisions author_id="x"}
#####
{/exp:entry_revisions}
```
**entry_id [Optional]**: Entry ID to get the revisions. You can use the pipe character (”|”) to query by multiple entry IDs.
```
{exp:entry_revisions entry_id="1|2|3"}
#####
{/exp:entry_revisions}
```
**site_id [Optional]**: Default will be current site.
```
{exp:entry_revisions site_id="1"}
#####
{/exp:entry_revisions}
```
**url_title [Optional]**: URL title of entry which revisions will be fetched.
```
{exp:entry_revisions url_title="xyz"}
#####
{/exp:entry_revisions}
```
**status [Optional]**: Entry status. Default = "open". You can use the pipe character ("|") to query by multiple statuses.
```
{exp:entry_revisions status="open|closed"}
#####
{/exp:entry_revisions}
```

**limit [Optional]**: Default = 10
```
{exp:entry_revisions limit="3"}
#####
{/exp:entry_revisions}
```
**version_date_sort [Optional]**: asc/desc. Default = desc
```
{exp:entry_revisions version_date_sort="asc"}
#####
{/exp:entry_revisions}
```
# Variables
**{revision:title}**: Title of entry revision.

**{revision:url_title}**: URL Title of entry revision.

**{revision:count}**: Revision counts - 1, 2, 3 ....

**{revision:total_counts}**: Total number of revisions.

**{revision:version_date format="%Y %m %d"}**: Entry revision date. See Date Variable Formatting for more information.

**{revision:entry_id}**: Entry ID

**{revision:custom_field_name}**: You can get the custom field’s value for entry revisions. It will not work for the field type which stores data separately within its own database tables like Relationship, Matrix, Grid, Image, File Grid, Fluid etc.

# Example
```
{exp:entry_revisions channel=“blogs|news” site_id=“1” author_id=“1” status=“open|closed”}
{if no_results}
No revisions
{/if}

Title: {revision:title}

Revision date: {revision:version_date format='%Y-%m-%d@%H:%i'}

Entry ID: {revision:entry_id}

URL Title: {revision:url_title}

Your Name: {if revision:your_full_name} {revision:your_full_name} {/if}
{/exp:entry_revisions}
```
