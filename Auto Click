import ctypes
import time
import keyboard

def ini():
    print('''
************************************************************************************************************
非商业与非法用途：严禁将此文件夹及其内容用于任何商业或非法用途。对于因违反此规定而产生的任何法律后果，用户需自行承担全部责任。
本程序按【~】按键开启自动拾取，再次按下即可关闭。在开启自动拾取之后即可按空格开始洗地"
************************************************************************************************************
''')


SendInput = ctypes.windll.user32.SendInput
PUL = ctypes.POINTER(ctypes.c_ulong)

control_number = [1]

def control_change():
    if control_number[0] == 1:
        control_number[0] = 0
        print("自动拾取已关闭")
    else:
        control_number[0] = 1
        print("自动拾取已开启")

def PressKey(hexKeyCode):
    extra = ctypes.c_ulong(0)
    ii_ = Input_I()
    ii_.ki = KeyBdInput(0, hexKeyCode, 0x0008, 0, ctypes.pointer(extra))
    x = Input(ctypes.c_ulong(1), ii_)
    ctypes.windll.user32.SendInput(1, ctypes.pointer(x), ctypes.sizeof(x))

def ReleaseKey(hexKeyCode):
    extra = ctypes.c_ulong(0)
    ii_ = Input_I()
    ii_.ki = KeyBdInput(0, hexKeyCode, 0x0008 | 0x0002, 0, ctypes.pointer(extra))
    x = Input(ctypes.c_ulong(1), ii_)
    ctypes.windll.user32.SendInput(1, ctypes.pointer(x), ctypes.sizeof(x))

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

class KeyBdInput(ctypes.Structure):
    _fields_ = [("wVk", ctypes.c_ushort),
                ("wScan", ctypes.c_ushort),
                ("dwFlags", ctypes.c_ulong),
                ("time", ctypes.c_ulong),
                ("dwExtraInfo", PUL)]


class HardwareInput(ctypes.Structure):
    _fields_ = [("uMsg", ctypes.c_ulong),
                ("wParamL", ctypes.c_short),
                ("wParamH", ctypes.c_ushort)]


class MouseInput(ctypes.Structure):
    _fields_ = [("dx", ctypes.c_long),
                ("dy", ctypes.c_long),
                ("mouseData", ctypes.c_ulong),
                ("dwFlags", ctypes.c_ulong),
                ("time", ctypes.c_ulong),
                ("dwExtraInfo", PUL)]


class Input_I(ctypes.Union):
    _fields_ = [("ki", KeyBdInput),
                ("mi", MouseInput),
                ("hi", HardwareInput)]


class Input(ctypes.Structure):
    _fields_ = [("type", ctypes.c_ulong),
                ("ii", Input_I)]




if __name__ == '__main__':
    ini()
    keyboard.add_hotkey('`', control_change)
    keyboard.add_hotkey('space', space_on_pressed)
    keyboard.wait()
