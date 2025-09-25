# Ex-1-Developing-AI-Agent-with-PEAS-Description

**Name:** Shanthosh G 

**Register Number:** 2305003008

## Aim:

To find the PEAS description for the given AI problem and develop an AI agent.

## Theory :

PEAS stands for:
```
P-Performance measure

E-Environment

A-Actuators

S-Sensors
```

It’s a framework used to define the task environment for an AI agent clearly.


## Pick an AI Problem


**1.** Self-driving car

**2.** Chess playing agent

**3.** Vacuum cleaning robot

**4.** Email spam filter

**5.** Personal assistant (like Siri or Alexa)

## Developing AI Agent with PEAS Description – Personal Assistant

### Agent: Personal Assistant Agent (Command-based, user-interactive)

**Performance Measure:**

Provides correct and relevant responses to user commands.

Minimizes response time (fast execution).

Executes valid tasks (time, date, reminders, music, website opening, etc.).

Maintains conversation context and user satisfaction.

Avoids invalid or meaningless responses.

**Environment:**

User’s digital environment (PC, phone, or smart device).

Receives input as text/voice commands.

Can access system clock, apps, internet browser, media player, reminders.

Fully observable in terms of user’s last command and current system status.

**Actuators:**

Displays or speaks responses to user queries.

Executes system-level actions (open browser, play music, set reminders).

Sends notifications/alerts (e.g., reminder messages).

Updates current state (e.g., stores reminders, logs commands).

**Sensors:**

Captures user input (text/voice commands).

Detects time and date from the system.

Observes user history (previous commands).

Monitors task completion status (whether reminder is set, music is playing, etc.).

## Algorithm:

**Step 1:** Initialize the assistant by setting its name (e.g., SmartAssistant) and greeting the user.

**Step 2:** Define the list of possible user commands (e.g., tell time, tell date, open website, set reminder, play music, do nothing).

**Step 3:** Repeat the following steps until the user quits:

3.1. Accept input from the user (text/voice command).

3.2. Identify the type of command:

If it contains "time" → fetch and display system time.

If it contains "date" → fetch and display today’s date.

If it contains "open" → open the specified website in the browser.

If it contains "remind" → store/display a reminder.

If it contains "music" → play music.

If it contains "nothing" → stay idle.

Else → display “Command not recognized.”

3.3. Execute the action using actuators (speak/print or open apps).

3.4. Optionally, log the command and response for reference.

**Step 4:** Continue interaction until the user explicitly says “quit” or “exit.”

**Step 5:** When quitting, display a farewell message and stop execution.

### Example Program:
```
class VacuumCleanerAgent:
    def __init__(self):
        # Initialize the agent's state (location and dirt status)
        self.location = "A"  # Initial location (can be "A" or "B")
        self.dirt_status = {"A": False, "B": False}  # Initial dirt status (False means no dirt)

    def move_left(self):
        # Move the agent to the left if possible
        if self.location == "B":
            self.location = "A"

    def move_right(self):
        # Move the agent to the right if possible
        if self.location == "A":
            self.location = "B"

    def suck_dirt(self):
        # Suck dirt in the current location if there is dirt
        if self.dirt_status[self.location]:
            self.dirt_status[self.location] = False
            print(f"Sucked dirt in location {self.location}")

    def do_nothing(self):
        # Do nothing
        pass

    def perform_action(self, action):
        # Perform the specified action
        if action == "left":
            self.move_left()
        elif action == "right":
            self.move_right()
        elif action == "suck":
            self.suck_dirt()
        elif action == "nothing":
            self.do_nothing()
        else:
            print("Invalid action")

    def print_status(self):
        # Print the current status of the agent
        print(f"Location: {self.location}, Dirt Status: {self.dirt_status}")
```

### Example usage:

```
agent = VacuumCleanerAgent()
```

### Move the agent, suck dirt, and do nothing

```
agent.perform_action("left")
agent.print_status()
agent.perform_action("suck")
agent.print_status()
agent.perform_action("nothing")
agent.print_status()
```

### Sample Output:

<img width="570" height="77" alt="image" src="https://github.com/user-attachments/assets/70bf8483-1b65-46d6-ab8b-eeda6d591f36" />


## Program:

```
import datetime
import webbrowser

class PersonalAssistantAgent:
    def __init__(self):
        self.name = "SmartAssistant"
        print(f"Hello! I am {self.name}, your personal assistant.")

    # Actions (Actuators)
    def tell_time(self):
        now = datetime.datetime.now().strftime("%H:%M:%S")
        print(f"The current time is {now}")

    def tell_date(self):
        today = datetime.date.today().strftime("%B %d, %Y")
        print(f"Today's date is {today}")

    def open_website(self, url):
        print(f"Opening {url} ...")
        webbrowser.open(url)

    def set_reminder(self, task, time):
        print(f"Reminder set: '{task}' at {time}")

    def play_music(self):
        print("Playing music... (Demo Mode)")

    def do_nothing(self):
        print("Okay, doing nothing.")

    # Perceive and Act
    def perform_action(self, command):
        command = command.lower()

        if "time" in command:
            self.tell_time()
        elif "date" in command:
            self.tell_date()
        elif "open" in command:
            site = command.replace("open", "").strip()
            if site:
                self.open_website(f"https://{site}")
            else:
                print("Please specify a website to open.")
        elif "remind" in command:
            self.set_reminder("Meeting", "6:00 PM")  # Demo
        elif "music" in command:
            self.play_music()
        elif "nothing" in command:
            self.do_nothing()
        else:
            print("Sorry, I didn't understand that command.")
```
### Usage: 

```
assistant = PersonalAssistantAgent()

assistant.perform_action("time")
assistant.perform_action("date")
assistant.perform_action("open google.com")
assistant.perform_action("remind me to study")
assistant.perform_action("play music")
assistant.perform_action("nothing")

```
### Output:

<img width="706" height="165" alt="image" src="https://github.com/user-attachments/assets/f1fcffa9-24a6-4a7e-a8af-2af6d5ebd921" />


### Result:

The program has been successfully implemented and performs the intended tasks as designed.
