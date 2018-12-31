# Journal
Journal script
import journalz

def main():
    print_header()
    run_event_loop()



def print_header():
    print(".....................")
    print("    Journal App")
    print(".....................")
    print()

def run_event_loop():

    print("What would you like to do?")
    cmd = "empty"

    journal_name = "default"
    journal_data = journalz.load(journal_name)

    while cmd != 'x' and cmd:
        cmd = input("[L]ist entries, [A]dd and entry, E[x]it: ")
        cmd = cmd.lower().strip()

        if cmd == "l":
            list_entries(journal_data)
        elif cmd == "a":
            add_entries(journal_data)
        elif cmd != "x" and cmd:
            print("sorry we dont understand '{}' ".format(cmd))

    print("Done, goodbye")
    journalz.save(journal_name, journal_data)


def list_entries(data):
    print("Your Journal entries:")
    entries = reversed(data)
    for idx,entry in  enumerate (entries):
     print("* [{}] {}".format(idx+1,entry))


def add_entries(data):
    text = input("type your entry, <enter> to exit: ")

    journalz.add_entry(text, data)
    #data.append(text)











main()

if __name__ == '__main__':
    main()
