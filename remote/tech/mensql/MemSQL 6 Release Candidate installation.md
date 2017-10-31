[http://www1.memsql.com/release-candidate-thank-you.html](http://www1.memsql.com/release-candidate-thank-you.html)

[<span style="color: rgb(51,122,183);background-color: transparent;font-size: 14px;font-family: Roboto, sans-serif;">https://docs.memsql.com/</span>](https://docs.memsql.com/)

<span style="color: rgb(79,79,79);background-color: rgb(255,255,255);font-size: 45px;font-family: freight-sans-pro, lato, sans-serif;">Thank You</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 24px;font-family: freight-sans-pro, lato, sans-serif;">To get started with MemSQL 6 Release Candidate, install or upgrade.</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 26px;font-family: freight-sans-pro, lato, sans-serif;">Installation Instructions:</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">Follow these instructions to install MemSQL on a single machine with no existing MemSQL components. If you wish to upgrade to MemSQL 6 RC from MemSQL 5.8, refer to the offline upgrade instructions below.</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">**1) Install MemSQL Ops**</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">To download MemSQL Ops 6 RC, click on </span>[<span style="color: rgb(38,171,226);background-color: rgb(255,255,255);font-size: 13px;font-family: freight-sans-pro, lato, sans-serif;">http://download.memsql.com/memsql-ops-6.0.0-rc2/memsql-ops-6.0.0-rc2.tar.gz</span>](http://download.memsql.com/memsql-ops-6.0.0-rc2/memsql-ops-6.0.0-rc2.tar.gz)

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">`tar xzf memsql-ops-6.0.0-rc2.tar.gz`</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">`cd memsql-ops-6.0.0-rc2`</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">`sudo ./install.sh -n`</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">**2) Install MemSQL 6 RC**</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">`memsql-ops memsql-deploy --role master --port 3306 --version-hash``**e31035268dd49e76d61a376f764c6a2eaf8a8bcf**`</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">Press ENTER at the prompt “If you would like to use the Community edition, just press enter:”.</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">`memsql-ops memsql-deploy --role leaf --port 3308 --version-hash``**e31035268dd49e76d61a376f764c6a2eaf8a8bcf**`</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">To verify you have the correct version, enter at the command prompt:  `memsql -e 'select @@memsql_version'` and the result should be 6.0.5.</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;font-family: freight-sans-pro, lato, sans-serif;">Offline Upgrade Instructions:</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">This upgrade process is offline. An offline upgrade shuts down the entire cluster for the duration of the upgrade. There is no online upgrade option available for MemSQL 6.0 RC.</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 18px;font-family: freight-sans-pro;">**Prior to performing the offline upgrade, we recommend backing up all cluster databases.**</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">Follow these instructions to both upgrade MemSQL Ops 5.8 to MemSQL Ops 6.0 and to upgrade MemSQL 5.8 to MemSQL 6.0 RC.</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">For more information about upgrading, see </span>[<span style="color: rgb(38,171,226);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">Upgrading MemSQL</span>](https://docs.memsql.com/operational-manual/v6.0-beta/upgrading-memsql/)<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">.</span>

## <span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 30px;font-family: freight-sans-pro, lato, sans-serif;">**Steps to Upgrade:**</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">**1) Upgrade MemSQL Ops**</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">Run:  `memsql-ops agent-upgrade --version 6.0.0-rc2`</span>

<span style="color: rgb(0,0,0);background-color: rgb(255,255,255);font-size: 18px;font-family: freight-sans-pro, lato, sans-serif;">**2) Upgrade MemSQL**</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">Execute the following command: `memsql-ops memsql-upgrade --version-hash e31035268dd49e76d61a376f764c6a2eaf8a8bcf`</span>

<span style="color: rgb(112,112,112);background-color: rgb(255,255,255);font-size: 20px;font-family: freight-sans-pro, lato, sans-serif;">Note: This command will shutdown the entire cluster for the duration of the upgrade.</span>