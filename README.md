# Home Assistant + ESPHome + Microsoft Teams = standing desk control

A Home Assistant &amp; ESPHome solution for having your desk raise whenever you join a Microsoft Teams meeting.

This solution builds on top of my original method which relied on sending a shell command to a Raspberry Pi, which in turn used a Bluetooth dongle to control the desk.
https://www.loryanstrant.com/2022/04/25/automatically-raise-your-desk-when-joining-a-microsoft-teams-call-or-meeting/

The code provided here is specific to my requirements as I have two powered standing desks in my home, however you can easily adapt to your needs.


## The files

### garage-desk.yaml & study-desk.yaml
These two are identical except for the names - so pick one and go with it.
You'll need to adjust the substitutions to match your preferred device name as well as heights.
The "common_settings.yaml" reference is simply where I park common sensors I want across all my ESPHome devices, as well as WiFi settings, API key, etc. Replace this with your specifics.

![image](https://user-images.githubusercontent.com/51473494/216590332-658c9f82-ef78-4619-b80f-28f005d33bfd.png)



![image](https://user-images.githubusercontent.com/51473494/216590552-1c7de17b-3b3c-4a57-bfa8-a93f8fbf6678.png)


### templates.yaml
Contains the code used to create sensors to track the desk status, as well as amount of time standing that day between both desks (as I some days go between both rooms).

![image](https://user-images.githubusercontent.com/51473494/216590910-e14340ee-c67f-49f9-b743-cbf2324179de.png)


![image](https://user-images.githubusercontent.com/51473494/216591141-41954ffb-d02c-416b-9672-f7afae2a9f53.png)


### sensors.yaml
Includes the sensors that captures the time the desks spend in each status, as well as my occupancy of either room (using ESPresense).

![image](https://user-images.githubusercontent.com/51473494/216590762-17ab6857-a2fd-43b1-91cc-0dfb82014fc8.png)


![image](https://user-images.githubusercontent.com/51473494/216590856-36b72463-f52b-40de-a57c-a81c966ae0bc.png)



### lovelace.yaml
Only contains a single card to display a needle gauge for showing how much time was spent standing at either/both desks across the working day.
It uses a conditional card which will only show if I'm in the garage (as that's where the display is that it shows on).

![image](https://user-images.githubusercontent.com/51473494/216589490-cecfc52f-acf9-45c0-9bc2-709e0cee865b.png)


### automations.yaml
There is only a single workflow in here, which incorporates various conditions such as the Workday integration, which room I'm in, whether the desk is standing, and my Teams status.
Note that the workflow also calls to change my study tablet display (to show my family that I'm in a call/meeting) as well as changing my LED strip colour - so you'll need to remove or replace these.

![image](https://user-images.githubusercontent.com/51473494/216589895-9e7c4c5a-9fd2-4562-badd-3114801ff400.png)




# References & requirements (other than Home Assistant and ESPHome)
- https://community.home-assistant.io/t/desky-standing-desk-esphome-works-with-desky-uplift-jiecang-assmann-others/383790
- https://espresense.com/
- https://github.com/RogerSelwyn/O365-HomeAssistant
