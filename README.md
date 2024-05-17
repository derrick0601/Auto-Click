# Auto-Click
```
When running the app, will auto clike the keyboard according to programm setting.
This is just create for Game.
```

> Auto Click
> > Readme.md
> > Auto Click.py
> > Auto Click.EXE


## Readme.md
```
This file will introduce how to use this software and how to edit it.
```

## Auto Click.py
```
####Can Edit this file to create the program accroding your requirement.

####I import three libraries to write programs
import ctypes
import time
import keyboard

####If you want to change the frequency of clicking, you can edit here.
def space_on_pressed():
    if control_number[0] == 1:
        print('Program Running')
        for i in range(0, 100):
            PressKey(0x39)
            time.sleep(0.01)
            ReleaseKey(0x39)
            time.sleep(0.01)
        print('Finished')
    print("please enter the · first")

####If you want to edit the trigger for clicking, can edit here.
if __name__ == '__main__':
    ini()
    keyboard.add_hotkey('`', control_change)
    keyboard.add_hotkey('space', space_on_pressed)
    keyboard.wait()

```
