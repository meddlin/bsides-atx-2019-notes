ActivitiesCache.db
Sqlite database
Complete record of every application that ran
-- application names and timestamp
-- browsing activity nia in here too
-- deleting history from browser doesn't clear it from here

Background activity monitor
-- in the Fall 2017 release
-- stored in System hive of the registry
-- apps, user SID, timestamps
-- CCleaner doesn't touch this either, nor do most anti-forensics tools

RecentApps
-- apps, timestamps, and files accessed by application, up to 10

System Resource Usage Monitor (SRUM)
-- since Win 8.1
-- network activity, push notifications, etc.
-- anything ysing a lot of resources, and of course…
-- timestamps
-- unsure if you can turn this off??

The above are good thing for red teams to clean up after themselves with...unsure if it causes system instability


For a driver to load on Win10, you must submit to Windows HLK
-- actually goes to Microsoft
-- this is a LOT to
