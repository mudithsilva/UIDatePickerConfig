# UIDatePicker Configuration
Step by Step to Config UIDatePicker on your ViewController -  SWIFT

#### Step 01

Initialize UIDatePicker on your ViewController.

```
  let toDatePicker = UIDatePicker()
```

#### Step 02

Add Input view and Target for UITextField.

```
  func createDatePicker() {
        self.toDatePicker.datePickerMode = .date   // Change Picker type as you want
        self.toDatePicker.addTarget(self, action: #selector(toDatePickerChanged), for: .valueChanged) // Detect changes on DatePicker
        self.toDate.inputView = self.toDatePicker  // Connect TextField Input view
  }

```

#### Step 03

Add Selector for DatePicker ``.valueChange``

```
      @objc func toDatePickerChanged() {
      
       // Add your logic when value changes in UIDatePicker.
      
        let formatter = DateFormatter()
        formatter.dateFormat = "dd MMMM yyyy"  //MMM dd,yyyy
        self.toDate.text = formatter.string(from: self.toDatePicker.date)
        
        formatter.dateFormat = "yyyy-MM-dd"  //MMM dd,yyyy
        // Save data
     }

```

#### Step 04

Add ``inputAccessoryView`` to the TextField.

```
func addToolBar() {
        let toolbarToDate = UIToolbar()
        toolbarToDate.sizeToFit()
        
        let doneToDateButton = UIBarButtonItem(barButtonSystemItem: .done, target: nil, action: #selector(doneDateSelect))
        let spaceButton2 = UIBarButtonItem(barButtonSystemItem: UIBarButtonSystemItem.flexibleSpace, target: nil, action: nil)
        toolbarToDate.setItems([spaceButton2, doneToDateButton], animated: false)
        
        self.toDate.inputAccessoryView = toolbarToDate
    }

```

#### Step 05

Add Selector for Done Button.

```
  @objc func doneDateSelect() {
        self.view.endEditing(true)
   }

```

#### Step 06

Add ``addToolBar()`` and ``createDatePicker()`` to ``viewDidLoad()``

```
    override func viewDidLoad() {
        super.viewDidLoad()
        self.createDatePicker()
        self.addToolBar()
    }

```
