# microsoftdate.today

Ever wanted to know the current date in Microsoft Exchange era? Now you can!

[https://microsoftdate.today](https://microsoftdate.today)

## Background

Self-hosted instances of Microsoft Exchange had a problem in their malware scanner, regarding parsing of dates.
Dates were stored as a `signed int32`, formatted in `yymmddHHMM` - since the biggest value of 32bit integers is `2147483647`, this parsing would fail for **any** date of year 2022, resulting in an integer overflow, a malfunctioning malware scanner and therefor e-mails not being sent or received.

Microsoft "fixed" this issue in a [quick-fix](https://techcommunity.microsoft.com/t5/exchange-team-blog/email-stuck-in-exchange-on-premises-transport-queues/ba-p/3049447) by altering the date format in a way, where January the 1st of 2022 is written as December 33rd of 2021.