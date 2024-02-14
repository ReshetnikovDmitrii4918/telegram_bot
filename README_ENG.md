## Telegram bot
**Description**

Telegram bot. This bot was created so that users could monitor their well-being in several convenient formats, as for some people, a simple data table may be much more convenient and informative than constructed graphs. The Telegram bot also helps to monitor the health of all groups of people who need it or are simply interested, and you can also track your condition after workouts if you are an athlete. In terms of directly working with this bot, the user can communicate with it exclusively by pressing buttons, but if desired, they can also write to it themselves. If the user does not understand something, they can always read about it in the instructions. The bot is implemented in Python.

**Testing**

When entering a conversation with the bot, on the main screen, the user sees 4 main buttons, each with its unique functionality, as shown in Figure 1.

 ![image](https://user-images.githubusercontent.com/75118943/178711836-783905e6-75df-429d-8ee9-bb87fa473928.png)

Figure 1 – main buttons

When a user first interacts with the bot, they are likely to press the "Instructions" button to find out why this bot is needed and which buttons to press at what moment to achieve the desired result according to Figure 2.

 ![image](https://user-images.githubusercontent.com/75118943/178711763-3bea5009-ea87-4d61-84ae-de8f9f1d3b04.png)

Figure 2 – "Instructions" button 

The user may encounter a situation where the lower buttons disappear and are not visible, then they will not understand what is happening and will try to send a message and receive recommendations for action according to Figure 3.

 ![image](https://user-images.githubusercontent.com/75118943/178711483-91ba1275-546d-4991-8fa2-1e61f9c1239b.png)

Figure 3 - unrecognizable message

After the user has read the instructions and understood everything, he tries to enter his data into the table by clicking on the "Enter Data" button. Next, he sees several new inline buttons with different topics in front of him, and he needs to click on the button indicating the condition for which he wants to enter data into the table according to Figure 4. After pressing the button, the user sees several more inline buttons, and by clicking on one of them, he determines the specific condition of the part of the body that was selected by the previous button. After choosing the specific condition, the data is entered into the file according to Figure 5. In the .csv file itself, the message time with the date is automatically determined, as well as the atmospheric pressure and temperature in St. Petersburg according to Figure 6.

 ![image](https://user-images.githubusercontent.com/75118943/178711317-3a412cb1-7b6b-41be-99fb-9c44f077da08.png)

Figure 4 - "Enter Data" button

 ![image](https://user-images.githubusercontent.com/75118943/178711272-a527180b-a677-46af-8137-57469c3138eb.png)

Figure 5 - Direct assessment of the condition

 ![image](https://user-images.githubusercontent.com/75118943/178709938-7b27f4dc-564e-43c3-9f5f-d0ff32d8572c.png)

Figure 6 - .csv file

When filling in their data at specific times and interacting with the bot, the user can receive a report on their condition for a given period. To do this, following the instructions, they need to click on the "Send me a report" button, after which they will receive a .csv file and two graphs showing the dependence of well-being on temperature and atmospheric pressure, as shown in Figure 7.

 ![image](https://user-images.githubusercontent.com/75118943/178710166-04f51c1e-3fb1-4b66-a3cb-41a0e2dffeeb.png)

Figure 7 - "Send me a report" button


Additionally, if the user wants to start the bot over, fill in a new table, and forget all the old data, they should click on the "Make the table empty" button. Then the .csv file will become empty and can be filled in again according to Figure 8.

![image](https://user-images.githubusercontent.com/75118943/178709485-ef13766b-9451-4a67-b556-cb9fcaeac14f.png)

Figure 8 – empty .csv file


