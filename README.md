# Library Management System

A beginner-friendly, straightforward Library Management System built with PHP and MySQL. This project is perfect for understanding basic CRUD (Create, Read, Update, Delete) operations, database relations, and user authentication in PHP without the complexity of large frameworks.

## 🌟 Features

*   **Authentication:** User login, registration, and logout with secure session management.
*   **Dashboard Overview:** See total books, authors, members, and overdue books at a glance.
*   **Book Management:** Add, edit, view, and delete books and track total vs. available copies.
*   **Author & Member Management:** Manage library members and book authors.
*   **Issue & Return System:** Issue books to members, track due dates, and handle returns.
*   **Overdue Tracking:** Automatically flag books that have passed their due dates.

## 🛠️ Built With

*   **Backend:** Procedural PHP 
*   **Database:** MySQL (`mysqli` extension)
*   **Frontend:** HTML, CSS, JavaScript (Vanilla)
*   **Icons:** FontAwesome

---

## 🗄️ Database Schema

The database consists of five main tables. The schemas are located in the `database/` folder.

| Table Name | Source File | Description | Primary Key | Key Columns / Foreign Keys |
| :--- | :--- | :--- | :--- | :--- |
| **`users`** | `user_schema.sql` | Handles authentication for staff and admins. | `user_id` | `username`, `email`, `password_hash`, `role` |
| **`authors`** | `library_db.sql` | Stores information about book authors. | `author_id` | `first_name`, `last_name`, `bio` |
| **`books`** | `library_db.sql` | Stores the library's catalog. | `book_id` | `title`, `isbn`, `category`, `total_copies`, `available_copies`<br>*(FK: `author_id` → `authors`)* |
| **`members`** | `library_db.sql` | Stores registered members (borrowers). | `member_id` | `full_name`, `email`, `phone` |
| **`issued_books`** | `library_db.sql` | Tracks the check-out and return process. | `issue_id` | `issue_date`, `due_date`, `return_date`, `status`<br>*(FK: `book_id` → `books`)*<br>*(FK: `member_id` → `members`)* |

*Note: A default admin account is created with Username: `admin`, E-mail: `admin@library.local` Password: `admin123`*

---S

## 🚀 Getting Started

Follow these instructions to get a copy of the project up and running on your local machine for development and testing.

### Prerequisites

You will need a local web server to run PHP and MySQL. Some popular options:
*   [XAMPP](https://www.apachefriends.org/index.html) (Windows, Mac, Linux)
*   [WAMP](https://www.wampserver.com/en/) (Windows)
*   [MAMP](https://www.mamp.info/en/) (Mac)

### Installation

**1. Copy the Files**
Place the `Library-management-system` folder inside your local server's public directory. 
*   For XAMPP: `C:/xampp/htdocs/`
*   For WAMP: `C:/wamp/www/`

**2. Setup the Database**
1. Open your web server control panel (e.g., XAMPP) and start **Apache** and **MySQL**.
2. Open your browser and go to `http://localhost/phpmyadmin`
3. Click on **Databases** and create a new database named `library_db`.
4. Go to the **Import** tab.
5. Click **Choose File** and select `database/library_db.sql` from your project folder. Click **Import**.
6. Repeat the process to import `database/user_schema.sql` (this gives you the admin login).

**3. Database Configuration (If needed)**
By default, local servers use the username `root` and an empty password. 
If your database has a different username or password, you can update it in the configuration file:
*   Open `config/db.php`
*   Change `$db_user` and `$db_pass` to match your credentials.

**4. Run the Application**
Open your web browser and navigate to the project folder:
`http://localhost/Library-management-system/`
*(You can login using Username: `admin`, E-mail: `admin@library.local` and Password: `admin123`)*

## 📂 Project Structure

*   `assets/` - Contains CSS files for styling and JavaScript for form validation.
*   `auth/` - Scripts handling login, logout, and registration.
*   `authors/` - CRUD files for managing authors.
*   `books/` - CRUD files for managing books.
*   `config/` - Database connection (`db.php`) and dynamic URL routing (`paths.php`).
*   `database/` - Contains the `.sql` files (`library_db.sql`, `user_schema.sql`) to set up tables.
*   `includes/` - Reusable components like the sidebar (`header.php`), footer, and session checks (`auth.php`).
*   `issue_return/` - Logic for checking out and returning library books.
*   `members/` - CRUD files for managing members.

## 📝 Usage Notes

*   **Dynamic Paths:** The app is designed to work whether you put it in the root folder or a subfolder thanks to `config/paths.php`. 
*   **Security:** This app uses basic authentication and procedural PHP. While great for learning and small projects, if deploying to a live production server, consider implementing further protections against SQL injection and CSRF attacks.
