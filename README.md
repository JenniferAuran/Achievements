# Achievements
Projects and achievements for 2023

## Software Chatbot Topic

## Hardware Check-in App
- **The PowerApp**
- I built a Power App for the frontend of hardware check-in for asset management.

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

- **Images**
![Hardware_UI](/Images/Hardware_UI.PNG)