#Ntjie Magongwa
from datetime import datetime
events = []

#sorts the list and reads the list out
def list_events():
    if not events:
        print("No events found.")
        return
#used lambda instead of a normal function. Just testing things out.
    sorted_events = sorted(events, key=lambda x: (x['date'], x['time']))
    for event in sorted_events:
        print(
            f"Title: {event['title']}, Description: {event['description']}, Date: {event['date'].strftime('%Y-%m-%d')}, Time: {event['time'].strftime('%H:%M')}")

#can only search by title not keyword
def eventName_search (title):
        exist_events = [event for event in events if event['title'] == title]
#if the title searched exist
        if exist_events:
            for event in exist_events:
                print(f"Title: {event['title']}, Description: {event['description']}, Date: {event['date'].strftime('%Y-%m-%d')}, Time: {event['time'].strftime('%H:%M')}")
        else:
            print(f"No Event for '{title}' was found.")
            print("Events available:")
            for event in events:
                print(f"Title: {event['title']}, Description: {event['description']}, Date: {event['date'].strftime('%Y-%m-%d')}, Time: {event['time'].strftime('%H:%M')}")


#adds new events
def add_event(title, description, date, time):
    #append so that the data  is added at the end of list
    events.append({
        'title': title,
        'description': description,
        'date': date,
        'time': time
    })
    print(f"Event '{title}' added successfully.")

#delete events
def delete_event(title):
    #events is the array variable that is initiated outside the function, therefore it is advice to call it with global
    global events
    events_before = len(events)
    events = [event for event in events if event['title'] != title]

    if len(events) < events_before:
        print(f"Event '{title}' deleted successfully.")
    else:
        print(f"No Event for '{title}' was found.")


#edit the events by the users preference.
def edit_event(title):
    for event in events:
        if event['title'] == title:
            print("Select what you would like to edit:")
            print("1. Title")
            print("2. Description")
            print("3. Date")
            print("4. Time")
            choice = input("Enter your choice:\t")
# User selection
            if choice == '1':
                new_title = input("Enter new title:\t")
                event['title'] = new_title
            elif choice == '2':
                new_description = input("Enter new description:\t")
                event['description'] = new_description
            elif choice == '3':

                while True:
                    try:
                        new_date_str = input("Enter new date (YYYY-MM-DD):\t")
                        new_date = datetime.strptime(new_date_str, '%Y-%m-%d')
                        event['date'] = new_date
                        break
                    except ValueError:
                        print("try again!!")
            elif choice == '4':
                while True:
                    try:
                        new_time_str = input("Enter new time (HH:MM):\t")
                        new_time = datetime.strptime(new_time_str, '%H:%M').time()
                        event['time'] = new_time
                        break
                    except ValueError:
                        print("try again!!")
            else:
                print("Invalid choice.")

            print("Event details updated successfully.")
            print(f"Title: {event['title']}, Description: {event['description']}, Date: {event['date'].strftime('%Y-%m-%d')}, Time: {event['time'].strftime('%H:%M')}")
            return

        print(f"No Event for '{title}' was found.")
        print("Events available:")
        for event in events:
            print(
                f"Title: {event['title']}, Description: {event['description']}, Date: {event['date'].strftime('%Y-%m-%d')}, Time: {event['time'].strftime('%H:%M')}")

#main function
def main():

    code_run = 'Y'
    while code_run == 'Y':

        print("\nEvent Schedular\n")

        print("1. Add Event")
        print("2. List Events")
        print("3. Delete Event")
        print("4. Edit Event")
        print("5. Search")
        print("6. Exit")
        choice = input("Enter choice:\t")

        if choice == '1':
            title = input("Enter title:\t")
            description = input("Enter description:\t")

            while True:
                try:
                    date_str = input("Enter date (YYYY-MM-DD):\t")
                    date = datetime.strptime(date_str, '%Y-%m-%d')
                    break
                except ValueError:
                    print("try again!!")




            while True:
                try:
                    time_str = input("Enter time (HH:MM):\t")
                    time = datetime.strptime(time_str, '%H:%M').time()
                    break
                except ValueError:
                    print("try again!!")

            add_event(title, description, date, time)
        elif choice == '2':
            list_events()
        elif choice == '3':
            title = input("Enter title of the event to delete:\t")
            delete_event(title)
        elif choice == '4':
            title = input("Enter title of the event to Edit:\t")
            edit_event(title)

        elif choice == '5':
            title = input("Enter an event name to search:\t")
            eventName_search(title)

        elif choice == '6':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")


        code_run = input("Do you want to go back to the main menu (Y/N):\t").upper()



        while code_run != 'Y' and code_run != 'N':
            code_run = input("Please use (Y/N)\nDo you want to go back to the main menu (Y/N):\t").upper()
        if code_run == 'N':
            print("Exiting...")
            break




#call the main function for everything to work
main()


# ----Reference List------
# study_material
# geeksforgeeks.org,
# w3schools.com
# Stackoverflow


![Screenshot (7)](https://github.com/00General00/ESA-/assets/73006104/5ecc6dc0-55b2-4d78-b6c4-f71ee25fe843)

![Screenshot (8)](https://github.com/00General00/ESA-/assets/73006104/914fac02-5ecc-4a02-8599-019b3cdeb851)


![Screenshot (10)](https://github.com/00General00/ESA-/assets/73006104/3266c746-7ced-4602-8af9-ab5dff05a6c5)

![Screenshot (12)](https://github.com/00General00/ESA-/assets/73006104/c0dc10e0-5d5c-45af-812e-6113dec9fd7f)

![Screenshot (14)](https://github.com/00General00/ESA-/assets/73006104/7244264f-f4ce-489c-9de2-828ded06c0b2)

