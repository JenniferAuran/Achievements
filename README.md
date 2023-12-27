# Achievements
Projects and achievements for 2023

## Software Chatbot Topic

- **Images**

![Chatbot_Software](/Images/Chatbot_Software.PNG)

## Hardware Check-in App
- **The PowerApp**
- I built a Power App for the frontend of hardware check-in for asset management.

- **Mobile Hardware Screen**
- Here is the code for the Hardware Mobile screen submit button:

```
// Initialize trigger variables
UpdateContext({resetTrigger: false, formSuccess: false});

// When hitting Submit, execute the following
If(
    !IsBlank(Trim(UserName.Selected.DisplayName)) && 
    !IsBlank(First(BarcodeReader.Barcodes).Value) && 
    Hardware.Selected.Name <> "*",
    Concurrent(
        Patch(
            'Offboarding Asset Management',
            Defaults('Offboarding Asset Management'),
            {
                Title: Trim(UserName.Selected.DisplayName),
                Date: Date.SelectedDate,
                Hardware: Hardware.Selected.Name,
                SerialNumber: First(BarcodeReader.Barcodes).Value
            }
        ),
        Reset(UserName),
        Reset(Date),
        Reset(Hardware),
        Reset(SerialNumber),
        Reset(LastName),
        UpdateContext({formSuccess: true})
    ),
    Notify("Please fill in all required fields. Make sure to select a valid option for Name, Hardware or Serial Number.", NotificationType.Error)
);

// If form submission was successful, navigate to SuccessScreen
If(formSuccess, Navigate(SuccessScreen, ScreenTransition.None));

// Reset the context variables to clear the text input and Serial Number
UpdateContext({resetTrigger: true, formSuccess: false});
UpdateContext({resetTrigger: false});
```

- **Image**
- Here is an image of the Hardware Mobile screen UI

![Hardware_UI](/Images/Hardware_UI.PNG)

- **Hardware Computer Screen**
- This is code for the Submit button on the Hardware Computer screen

```
// Initialize trigger variables
UpdateContext({resetTrigger: false, formSuccess: false});

// When hitting Submit, execute the following
If(
    !IsBlank(Trim(UserName_2.Selected.DisplayName)) && 
    !IsBlank(First(BarcodeReader_1.Barcodes).Value) && 
    Hardware_3.Selected.Name <> "*",
    Concurrent(
        Patch(
            'Offboarding Asset Management',
            Defaults('Offboarding Asset Management'),
            {
                Title: Trim(UserName_2.Selected.DisplayName),
                Date: Date_2.SelectedDate,
                Hardware: Hardware_3.Selected.Name,
                SerialNumber: First(BarcodeReader_1.Barcodes).Value
            }
        ),
        Reset(UserName_2),
        Reset(Date_2),
        Reset(Hardware_3),
        Reset(SerialNumber_1),
        Reset(LastName_2),
        UpdateContext({formSuccess: true})
    ),
    Notify("Please fill in all required fields. Make sure to select a valid option for Name, Hardware or Serial Number.", NotificationType.Error)
);

// If form submission was successful, navigate to SuccessScreen
If(formSuccess, Navigate(SuccessScreen, ScreenTransition.None));

// Reset the context variables to clear the text input and Serial Number
UpdateContext({resetTrigger: true, formSuccess: false});
UpdateContext({resetTrigger: false});

```

- **Image**
- Here is the Hardware for Computer screen

![Hardware_Computer](/Images/Hardware_Computer.PNG)

## Mi-Fi Check-in App
- **The Mi-Fi Power App Screen**
- I built a screen into the Power App for the hardware check-in app for Mi-Fi management.
```
- This is the code for the submit button on the Mi-Fi check-in app

// Initialize trigger variables
UpdateContext({resetTrigger: false, formSuccess: false});

// Perform the data submission and check for errors
Set(varError, 
    IsError(
        Patch(
            'MiFi Submissions', 
            Defaults('MiFi Submissions'),
            {
                Title: MiFiName.Selected.Name,
                Date: Date_1.SelectedDate,
                'Last Name, First Name': Trim(UserName_1.Selected.DisplayName),
                // Swap the "Check-in" and "Check-out" text values to match the toggle's position
                Status: {
                    Value: If(CheckToggle.Value, "Check-out", "Check-in") // This assumes toggling to the right is "Check-out"
                }
            }
        )
    )
);

// If there was no error, navigate to SuccessScreen, else do something else (like showing an error message)
If(
    !varError,
    Navigate(SuccessScreen, Transition.None)
    // You can add an else clause here if you need to handle the error case
);

// Reset the input controls
Reset(UserName_1);
Reset(Date_1);
Reset(MiFiName);
Reset(LastName_1);

// Update the context variables to clear the text input and Serial Number
UpdateContext({resetTrigger: true, formSuccess: !varError});
UpdateContext({resetTrigger: false});

```
- **Image**
- **MiFi Checkin App Screen**

![Spencer Fane Custom Applications Menu](/Images/MiFi_Checkin_App.PNG)


  
- This is code for the buttons on the main page of the Spencer Fane Custom Applications Menu

```
// Navigation set for each button that will navigate to the live custom application

Navigate('Appeal Questionnaire',ScreenTransition.Fade)
Navigate('Email Access',ScreenTransition.Fade)
Navigate('Firm Groups',ScreenTransition.Fade)
Navigate('Location Access',ScreenTransition.Fade)
```
- **Image**
- Here is the Spencer Fane Custom Applications Menu

![Spencer Fane Custom Applications Menu](/Images/SF_Custom_Apps_Menu.PNG)
