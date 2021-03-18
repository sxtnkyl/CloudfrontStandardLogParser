## Goal

For use with low traffic websites. Can be used to locally store logs and keep S3 buckets decluttered. 
Parse Cloudfront standard logs for valid JSON objects, sort into folders by date, 
and create two compiled jsons (bots and unique viewers).

*NOTE: compile by bots and unique viewers currently separate*

### Setup

* AWS create credentials profile
* Connect to aws toolkit 
  *https://docs.aws.amazon.com/toolkit-for-vscode/latest/userguide/connect.html*
* Set global credentials file
* Set global config file
  *https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/global-config-object.html*
* Dotenv file should contain KEYID, SECRET, REGION, BUCKET  

### Javascript

#### **index.js**

Creates a folder in working directory by date(year, month, day). First arguement should be a number *keyAmount* of files 
to download from your S3 bucket, defined in dotenv. Starts by oldest file in the bucket. 

*NOTE: Bucket must not have files nested in folders*

```sh
node index.js 6
```

#### **filterFolder.js**

Optional usage- takes a folder of one day and organizes logs from bots from unique viewers 
into two json files (botVisits.json and visitorsByCip.json). Takes three arguements- year, month, and day.
Year must be 4 chars, while month and day are 2 chars. 

```sh
node filterFolder.js 2021 02 17
```