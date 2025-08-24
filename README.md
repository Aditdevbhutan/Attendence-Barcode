# Attendence-Barcode

### My Objectives 
- create a unique barcode for each student 
- student can come near the camera and the camera will dectect the student barcode  and put the studnet as present in the his own class (info required: name of studnet, class and section fo the studnet)
- separate app to create the barcode (web-based flask,html css) interconnected with the app/web app for the scaning and attedndece of the studnet 
- app to save the studnet data (save the data in a simple database )and do the attednece with the primary camera a save the data in .csv file with date and make a class wise sheet inside the smae the file
- the app should the modern 
- simple not complex 
### Roadmap
#### Phase 1: Plan Your System

Apps Required:

1. Barcode Generator App

- Web-based (Flask + HTML/CSS).

- Creates unique barcodes for each student.

- Saves student info (name, class, section) in a database.

2. Attendance Scanner App

- Python app with camera access.

- Reads barcodes via the primary camera.

- Marks attendance automatically.

- Saves attendance in a .csv file, with a separate sheet (or tab) per class.

2.1 Data Structure:

- Student DB (SQLite recommended for simplicity)

- Columns: id, name, class, section, barcode_id

- Attendance CSV

- Columns: date, barcode_id, name, class, section, status

#### Phase 2: Barcode Generator App (Web)

Steps:

Create a Flask project with pages:

- /add-student → form to input name, class, section.

- /generate-barcode → generates unique barcode using python-barcode or qrcode.

- /students → view all students and download their barcode.

Generate a unique ID for each student (can be UUID or auto-incremented ID).

Save student info in SQLite database.

Generate barcode image for each student and allow download/print.

Python Libraries Needed:

- flask

- python-barcode or qrcode

- sqlite3

Frontend:

Simple HTML/CSS interface with Bootstrap for a clean look.

#### Phase 3: Attendance Scanner App

Steps:

1. Capture camera input: Use OpenCV to access primary camera.

2. Read barcodes: Use pyzbar or opencv to detect and decode barcode.

3. Lookup student info: Query SQLite DB to get student name, class, section.

4. Save attendance:

- Save attendance in a .csv file for that date.

- For multiple classes, separate sheets (you can use pandas.ExcelWriter to create multiple sheets in one .xlsx).

- UI (optional): Minimal Tkinter window showing camera feed and detected student info.

##### Python Libraries Needed:

opencv-python

pyzbar

pandas

#### Phase 4: Connect Both Apps

- Database Sharing: Both apps use the same SQLite database.

- Barcode Scan → Attendance Update:

1. Scan barcode.

2. Lookup in DB.

3. Mark attendance in CSV for that student, date, and class.

#### Phase 5: Optional Enhancements

- Modern UI: Use Bootstrap + simple JS for generator app.

- Attendance Reports: View and download attendance reports class-wise.

- Login (optional): Admin login to manage students.

- Real-Time Updates: Show “Present” status immediately when scanned.

#### Phase 6: Project Structure Example

```
barcode_attendance/
│
├── barcode_generator_app/
│   ├── app.py          # Flask app
│   ├── templates/
│   │    ├── add_student.html
│   │    ├── students.html
│   └── static/
│        └── css/
│
├── attendance_scanner/
│   ├── scanner.py      # Python OpenCV scanner
│   ├── database.db     # SQLite DB shared with generator
│   └── attendance.xlsx
│
└── README.md

```

#### Phase 7: Learning Steps

1. Learn Flask forms & routes.

2. Learn barcode generation (python-barcode / qrcode).

3. Learn OpenCV camera capture + barcode detection (pyzbar).

4. Learn CSV / Excel handling (pandas).

5. Connect generator and scanner using the same DB.
