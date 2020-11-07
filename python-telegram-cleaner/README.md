# Quickly purge all messages for all users in Telegram group.

**This is a fork of [Message Cleaner](https://github.com/S0Ulle33/telegram-message-cleaner) by S0Ulle33. The main modification is that this script allows to quickly delete all messages from all group members for all group members. Also it gets api_id and api_hash from user input or system variables, but the possibility to use hardcoded value is left in code and commented.**

## Requirements

-   Python 3.6 or higher
-   Python libraries: 
    - `telethon`
    - `prettytable`

## Installing


* Clone it or download manually.
```shell
    git clone https://github.com/who609102/telegram-message-cleaner.git
    cd telegram-message-cleaner
```

* Install necessary libraries using system *pip*
```shell
    pip install -r requirements.txt
```
or using *pipenv*
```shell
    pipenv install
```

## Usage
General template: `telegram_message_cleaner.py [-s [id id ...]] [-d [id id ...]]`

Before working with Telegram’s API, you need to get your own API ID and hash:

1. Follow this [link](https://my.telegram.org/) and login with your phone number.
2. Click on the link `API Development tools`.
3. A *Create new application* window will appear. Fill in your application details. There is no need to enter any URL, and only the first two fields (*App title* and *Short name*) can currently be changed later.
4. Click on *Create application* at the end. Remember that your **API hash is secret** and Telegram won’t let you revoke it. Don’t post it anywhere!
5. Specify them in corresponding variables (`api_id` and `api_hash`) in `telegram_message_cleaner.py`


### Samples
* `python telegram_message_cleaner.py -h` to show the help
* `python telegram_message_cleaner.py -s` to show stats of messages for all group chats
   It will ask you Id/hash/phone for the first run ONLY (!)
* `python telegram_message_cleaner.py -s GROUP_CHAT_ID1 GROUP_CHAT_ID2` to show stats of messages for group chats with GROUP_CHAT_ID1 and GROUP_CHAT_ID2
* `python telegram_message_cleaner.py -d` to delete all messages in all group chats
* `python telegram_message_cleaner.py -d GROUP_CHAT_ID1 GROUP_CHAT_ID2` to delete all messages in group chats with GROUP_CHAT_ID1 and GROUP_CHAT_ID2


### Schedule as a task

#### Create scheduled tasks with Command Prompt on Windows 10(IN PROGRESS)
Windows 10 ships with Task Scheduler, which is an advanced tool that allows you to create and run routines automatically.
* `SCHTASKS /CREATE /SC DAILY /TN "MyTasks\TaskName" /TR "C:\Windows\System32\notepad.exe" /ST 05:00` to create a daily task 'MyTasks\TaskName' to run an app at 5:00 every day
* `SCHTASKS /CREATE /SC WEEKLY /D SUN /TN "MyTasks\TaskName" /TR "C:\Windows\System32\notepad.exe" /ST 05:00` to create a weekly task 'MyTasks\TaskName' to run an app at 5:00 every week
* `SCHTASKS /CHANGE /TN "MyTasks\TaskName" /ST 09:00` - change startup time of a scheduled task 'MyTasks\TaskName'
* `SCHTASKS /CHANGE /TN "MyTasks\TaskName" /DISABLE` - disable a scheduled task 'MyTasks\TaskName'
* `SCHTASKS /DELETE /TN "MyTasks\TaskName"` - delete a scheduled task 'MyTasks\TaskName'
* see more details https://docs.microsoft.com/en-us/previous-versions/orphan-topics/ws.10/cc772785(v=ws.10)

### Run it
###  How to run in docker(IN PROGRESS)
This sample demonstrates how to pack simple python application as docker image and run it
Go to `python-sample1` and run:
* `docker build -t telegramm-cleaner .` to build the image
* `docker image ls | grep telegramm` to see the images like "*python*"
* `docker run --rm telegramm-cleaner` to run the container from the image
* `docker run --name telegramm-cleaner-container -d --rm telegramm-cleaner` to run the named container from the image

#### Good commands
* `docker ps -qa` - list IDs of all containers
* `docker rm $(docker ps -qa)` - remove all existing containers
* `docker rmi $(docker images -q)` - remove all existing images
