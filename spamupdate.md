# spamupdate

This script is meant to be run via `cron` every 10 minutes so it can manage the `IMAP` based spam filtering and retraining folders. The spam filtering system itself is based on [SpamProbe]. The path to a users mailbox is typically `/home/u/DOMAINNAME/home/USERNAME/Maildir` where there can be a number of **optional** SpamProbe training folders outlined below. The presence of the `Junk` folder triggers most of the filtering actions, in other words if a `KeepSpam` folder exists but `Junk` does not then no spam will be saved to `KeepSpam`. Note that the spelling and case of these folders must be exactly as indicated.

## Junk

If the `Junk` folder exists then various spam filtering and management functions are enabled and this is where filtered spam messages end up. It is a managed folder in the sense that messages older than 24 hours are automatically removed. If this folder does not exist then no filtering, training or management takes place on any of the following folders so that the end user has control over whether SpamProbe filtering is enabled or not.

## KeepSpam

If this folder exists then any spam will be copied to this folder and not deleted. This is useful to build up a `corpus` of spam messages to pre-train other mail accounts via a `TrainSpam` folder. Your `Sent` folder is a good source of non-spam massages to feed into the `TrainGood` folder.

## IsGood

Incorrectly flagged good messages that end up in the `Junk` folder can be retrained by dragging them into this folder. After going through the retraining process the message will be moved to the `Inbox`.

## IsSpam

This is the most important and often used retraining folder for spams that end up in your `Inbox`. Drag (or move) spam messages from your `Inbox` to this folder and after a few minutes they will retrain the filtering system and be automatically removed from this folder. Try not to retrain old subscribed mailing list messages just because you no longer want them in your `Inbox`, always try to unsubscribe from them first.

## TrainGood

This folder can be used to **pre-train** good messages. Copying (not dragging or moving) messages from your `Sent` folder is a good option for this folder so the filtering system has a better idea what messages you consider 'good'. Messages will be removed after pre-training so make sure you **copy** any good messages so that you do not lose them.

## TrainSpam

Copy any and all genuine spam messages into this folder to help **pre-train** the filtering system to know about what you consider spam. These spam messages will be removed after pre-training the filtering system.

## UnSpam

Rarely used but in case you mis-train a message you can copy or move a message here to remove it from the filtering systems database.

## Reset

A special one-time usage folder that triggers a complete reset of the filtering folders and reinstalls a stock standard default filtering database. If you feel you have completely messed up the retraining database then you can simply create this `Reset` folder and that will remove your cuurent filtering database and install a "fresh" one. The folder will automatically removed after the reinstallation procedure.

## Backup

This is not strictly a filtering folder but comes with the system. If it exists then **ALL** mail will be added to this folder before any filtering takes place so it acts like a backup folder. However, it does not require the presence of the Junk folder to trigger its functionality as it can be useful in non-filtering situations too.

[SpamProbe]: http://spamprobe.sourceforge.net/
