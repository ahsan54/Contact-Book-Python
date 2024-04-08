# Contact-Book-Python

This repository contains a simple Python program for managing contacts or a "Khatta Book" digitally. It's implemented using Python's dictionary data structure with lists to store contacts.

## Features

- Add new contacts with names and phone numbers.
- View all contacts in the address book.
- Search for contacts by name(key) and also by (Value).
- Update existing contact information.
- Delete contacts from the address book.
- Update existing contact Name(Key).
- Update existing contact Number(Value).
- Add New Value in any contact
- Extend any contact

## Getting Started
clone: https://github.com/ahsan54/Contact-Book-Python.git

# Contributions
Contributions are welcome! If you find any bugs or have suggestions for improvements, feel free to open an issue or submit a pull request.

# License
  Make sure to adjust the content according to your specific implementation details and preferences.

## CODE
    import pyttsx3
voice = pyttsx3.init()
class A():
    def __init__(self):
        self.Dict = {}

    def Demand(self):
        voice.say("Welcome TO Contact Book!")
        voice.runAndWait()
        Dmnd = input("Enter Demand: ")
        Dmnd = int(Dmnd)

        for i in range(Dmnd):
            print("Enter Key : ", (i + 1))
            key = input()
            if key not in self.Dict:
                self.Dict[key] = []

            while True:
                print("Enter Value OR ---> press 'stop' to stop : ")
                value = input()
                if value.lower() == 'stop':
                    break
                self.Dict[key].append(value)

    def Update_Key_Name(self):
        Which_Key_To_Update = input("Enter Key To Update: ")
        if Which_Key_To_Update in self.Dict:
            New_Key = input("Enter New Key: ")
            self.Dict[New_Key]  = self.Dict.pop(Which_Key_To_Update)
            print(self.Dict)
        else:
            print("Key Not Found!")


    def Update_value_Name(self):
        Which_Value = input("Which Value?: ")

        for key, values in self.Dict.items():
            if Which_Value in values:
                print(f"Changing This Set:  '{key}': {values}")
                indx = values.index(Which_Value)
                NewValue = input(f"Enter New Value: ")
                self.Dict[key][indx] = NewValue
                break
        print("Updated Dictionary:", self.Dict)

    def Add_New_Value(self):
        WhichKey = input("Which-Key U Want To Add New Value: ")
        for key, value in self.Dict.items():
            if WhichKey in key:
                N_V = input("Enter New Value: ")
                self.Dict[key].append(N_V)
        print("Updated Dictionary:", self.Dict)

    def Delete_Any_Pair(self):
        KeyToDel = input("Enter Key To Delete: ")
        if KeyToDel in self.Dict.keys():
            self.Dict.pop(KeyToDel)
        print(self.Dict)

    def PrintKhatta(self):
        print(self.Dict)

    def Specific(self):
        inp = input("Enter Key To View Its Values: ")
        if inp in self.Dict:
            print(self.Dict[inp])

    def Add_New_Key(self):
        K_N = input("Enter Key Name: ")
        self.Dict.update({K_N: []})

        while True:
            VaL = input("Enter Value OR 'stop' to Exit:  ")
            if VaL == "stop":
                break
            self.Dict[K_N].append(VaL)
        print("Updated Khatta: ", self.Dict)


class Main:
    def Main(self):
        obj1 = A()
        obj1.Demand()

        while True:
            print("Enter 1 : For Updating Key-Name")
            print("Enter 2 : For Updating Value-Name")
            print("Enter 3 : For Deleting (Key_Value)Pair")
            print("Enter 4 : For Viewing Full Contacts")
            print("Enter 5 : For Printing Specific Key")
            print("Enter 6 : For Adding New Value")
            print("Enter 7 : For Extending Khatta")
            inp = input("Select  OR 'stop' To Terminate:  ")
            inp = int(inp)
            if inp == 'stop':
                break
            if inp == 1:
                obj1.Update_Key_Name()

            elif inp == 2:
                obj1.Update_value_Name()

            elif inp == 3:
                obj1.Delete_Any_Pair()

            elif inp == 4:
                obj1.PrintKhatta()

            elif inp == 5:
                obj1.Specific()

            elif inp == 6:
                obj1.Add_New_Value()

            elif inp == 7:
                obj1.Add_New_Key()


MainObject = Main()
MainObject.Main()
