# 📝 Django Sticky Notes App

A beautiful and functional personal Sticky Notes web application built with Django. Users can register, log in, and manage their own private collection of colorful notes.

![Django](https://img.shields.io/badge/Django-4.x-green)
![Python](https://img.shields.io/badge/Python-3.8+-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)

---

## 📋 Table of Contents

- [Features](#features)
- [Screenshots](#screenshots)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [URLs & Routes](#urls--routes)
- [Models](#models)
- [Bonus Features](#bonus-features)
- [Technologies Used](#technologies-used)
- [Troubleshooting](#troubleshooting)
- [Author](#author)

---

## ✨ Features

### Core Features
- ✅ **User Authentication** - Register, Login, Logout functionality
- ✅ **Create Notes** - Add new sticky notes with title, content, and color
- ✅ **Edit Notes** - Update existing notes
- ✅ **Delete Notes** - Remove notes with confirmation
- ✅ **View All Notes** - See all your notes in a beautiful grid layout
- ✅ **Colorful Notes** - Each note can have its own background color
- ✅ **Search Functionality** - Search notes by title or content
- ✅ **Responsive Design** - Works on desktop, tablet, and mobile
- ✅ **User Privacy** - Users can only see and manage their own notes

### Security Features
- 🔒 Login required for all note operations
- 🔒 CSRF protection on all forms
- 🔒 Users cannot access other users' notes
- 🔒 Password validation and hashing

---

## 📸 Screenshots

### Home Page - Notes List
```
+------------------------------------------+
|  📝 Sticky Notes              [User ▼]   |
+------------------------------------------+
|                                          |
|  My Notes                    [+ New Note]|
|  Total 5 notes hain                      |
|                                          |
|  [🔍 Search...] [Search]                 |
|                                          |
|  +-------------+  +-------------+        |
|  | 📋 Shopping |  | 💡 Ideas    |        |
|  | Milk, Eggs  |  | Project     |        |
|  | [✏️] [🗑️]  |  | ideas...    |        |
|  | Jan 15      |  | [✏️] [🗑️]  |        |
|  +-------------+  +-------------+        |
|                                          |
+------------------------------------------+
```

### Create/Edit Note
```
+------------------------------------------+
|  New Note                    [Back]      |
+------------------------------------------+
|                                          |
|  Title: [________________]               |
|                                          |
|  Content:                                |
|  [                              ]        |
|  [                              ]        |
|  [                              ]        |
|  0 characters                            |
|                                          |
|  Color: [🎨] Color choose karo           |
|                                          |
|  [Create Note]  [Cancel]                 |
|                                          |
+------------------------------------------+
```

---

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package installer)
- Git (optional, for cloning)

### Step 1: Clone or Download the Project

```bash
# Using Git
git clone <repository-url>
cd sticky_project

# Or download and extract the ZIP file
cd sticky_project
```

### Step 2: Create Virtual Environment (Recommended)

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install django
```

### Step 4: Run Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### Step 5: Create Superuser (Optional - for Admin Access)

```bash
python manage.py createsuperuser
```

Enter username, email (optional), and password when prompted.

### Step 6: Run the Development Server

```bash
python manage.py runserver
```

### Step 7: Access the Application

Open your browser and go to:
- **Main App**: http://127.0.0.1:8000/
- **Admin Panel**: http://127.0.0.1:8000/admin/

---

## 📖 Usage

### First Time Setup

1. **Register a new account**
   - Go to http://127.0.0.1:8000/register/
   - Enter username and password
   - Click "Register"

2. **Login**
   - Go to http://127.0.0.1:8000/login/
   - Enter your credentials
   - Click "Login"

### Managing Notes

#### Create a New Note
1. Click "New Note" button on the home page
2. Enter a title
3. Write your note content
4. Choose a color (optional - defaults to yellow)
5. Click "Create Note"

#### Edit a Note
1. Click the pencil icon (✏️) on any note card
2. Make your changes
3. Click "Save Changes"

#### Delete a Note
1. Click the trash icon (🗑️) on any note card
2. Confirm deletion on the confirmation page
3. Click "Ha, Delete Karo" to permanently delete

#### Search Notes
1. Type in the search box on the home page
2. Press Enter or click "Search"
3. Results will show notes matching title or content

---

## 📁 Project Structure

```
sticky_project/
│
├── manage.py                 # Django management script
├── db.sqlite3               # SQLite database (created after migration)
├── README.md                # This file
│
├── sticky_project/          # Project configuration
│   ├── __init__.py
│   ├── settings.py          # Project settings
│   ├── urls.py              # Project-level URLs
│   └── wsgi.py              # WSGI configuration
│
└── notes/                   # Main application
    ├── __init__.py
    ├── admin.py             # Admin panel configuration
    ├── apps.py              # App configuration
    ├── forms.py             # Form classes
    ├── models.py            # Database models
    ├── views.py             # View functions
    ├── urls.py              # App-level URLs
    │
    └── templates/           # HTML templates
        ├── base.html        # Base template
        ├── login.html       # Login page
        ├── register.html    # Registration page
        ├── note_list.html   # Notes list page
        ├── note_form.html   # Create/Edit note page
        └── note_confirm_delete.html  # Delete confirmation
```

---

## 🌐 URLs & Routes

| URL | Description | Login Required |
|-----|-------------|----------------|
| `/` | Home page (redirects to notes) | Yes |
| `/register/` | User registration | No |
| `/login/` | User login | No |
| `/logout/` | User logout | Yes |
| `/notes/` | List all notes | Yes |
| `/notes/new/` | Create new note | Yes |
| `/notes/<id>/edit/` | Edit note | Yes |
| `/notes/<id>/delete/` | Delete note | Yes |
| `/admin/` | Django admin panel | Yes (staff only) |

---

## 🗄️ Models

### Note Model

| Field | Type | Description |
|-------|------|-------------|
| `title` | CharField(max_length=200) | Note ka title |
| `content` | TextField | Note ka actual content |
| `color` | CharField(max_length=7) | Background color (hex) |
| `created_at` | DateTimeField | Creation timestamp |
| `updated_at` | DateTimeField | Last update timestamp |
| `owner` | ForeignKey(User) | Note ka owner |

---

## 🎁 Bonus Features

This project includes several bonus features beyond the basic requirements:

1. **🔍 Search Bar** - Search notes by title or content
2. **🎨 Color Picker** - Interactive color picker for note backgrounds
3. **📊 Character Counter** - Live character count in content field
4. **👁️ Live Preview** - See how your note will look while editing
5. **🔒 Password Toggle** - Show/hide password in login/register forms
6. **📱 Responsive Design** - Bootstrap 5 for mobile-friendly interface
7. **💬 Flash Messages** - Success/error notifications
8. **📅 Date Display** - Shows when note was last updated

---

## 🛠️ Technologies Used

### Backend
- **Django 4.x** - Python web framework
- **SQLite** - Default database
- **Python 3.8+** - Programming language

### Frontend
- **HTML5** - Markup language
- **CSS3** - Styling
- **Bootstrap 5** - CSS framework
- **Bootstrap Icons** - Icon library
- **JavaScript** - Client-side scripting

### Security
- **Django CSRF Protection** - Form security
- **Django Authentication** - User management
- **Password Hashing** - Secure password storage

---

## 🔧 Troubleshooting

### Common Issues

#### Issue: `ModuleNotFoundError: No module named 'django'`
**Solution:**
```bash
pip install django
```

#### Issue: `OperationalError: no such table: notes_note`
**Solution:**
```bash
python manage.py makemigrations
python manage.py migrate
```

#### Issue: `IntegrityError: UNIQUE constraint failed`
**Solution:** Username already exists. Try a different username.

#### Issue: Can't access admin panel
**Solution:** Create a superuser first:
```bash
python manage.py createsuperuser
```

#### Issue: Static files not loading
**Solution:** In development, Django serves static files automatically. For production, run:
```bash
python manage.py collectstatic
```

---

## 👨‍💻 Author

**Created for:** Web Developoment Mini Project  
**Institution:** National University of Computing and Emerging Sciences (FAST-NUCES)


### Assignment Details
- **Course:** Web Developoment
- **Assignment:** #02 - Django Assignment
- **Name :** Moeez Uddin
- **Roll Number :** 22P-9203
- **Project:** Sticky Notes App

---

## 📜 License

This project is created for educational purposes as part of a university assignment.

---

## 🙏 Acknowledgments

- Django Documentation: https://docs.djangoproject.com/
- Bootstrap 5: https://getbootstrap.com/
- Bootstrap Icons: https://icons.getbootstrap.com/

---

## 💡 Tips for Success

1. **Build incrementally** - Start with models, then views, then templates
2. **Use the admin panel** - Create a superuser to inspect your data
3. **Read error messages** - Django's debug page is very helpful
4. **Test frequently** - Run the server and test after each change
5. **Use version control** - Commit your changes regularly with Git

---

## 📞 Support

If you encounter any issues:
1. Check the troubleshooting section above
2. Read Django's official documentation
3. Search for solutions on Stack Overflow
4. Ask your instructor or classmates for help

---

**Happy Coding! 🚀**
