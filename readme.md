# Data Project Database

This repository contains SQL scripts and supporting files for creating a PostgreSQL database, managing database users, and loading IPL match data from CSV files into tables. The project is designed to demonstrate the basic operations of database setup, data import, and cleanup.

## Repository Structure

```
# scripts/
   createUserDatabase.sql         # Script to create a new user and database
   dropUserDatabase.sql           # Script to clean up the user and database
   load_ipl_data.sql              # Script to create tables and load data from CSV
                               
# data/
   matches.csv                    # IPL matches data
   deliveries.csv                 # IPL deliveries data

.gitignore                        # Files and directories to ignore in version control
README.md                         # Instructions for running the project

```

## Prerequisites

Ensure the following are installed on your system:
- PostgreSQL (version 12 or higher recommended)
- `psql` command-line client
- Git

## Getting Started

### 1. Clone the Repository

```bash
git clone https://gitlab.com/mountblue/31.4-java/utkarsh/data-project-database.git
cd data-project-database
```

### 2. Set Up the Database and User

Run the script to create a new database and user:

```bash
psql -U postgres -f scripts/createUserDatabase.sql
```

This script:
1. Creates a new PostgreSQL user (`ipl_user`).
2. Creates a new database (`ipl_database`).
3. Assigns ownership of `ipl_database` to `ipl_user`.

### 3. Load Data into the Database

To create the necessary tables and load the data from CSV files:

```bash
psql -d ipl_database -f scripts/load_ipl_data.sql
```

### 4. Verify the Data

After loading, you can verify the data with the following queries:

- Count rows in the `matches` table:
  ```sql
  SELECT COUNT(*) FROM matches;
  ```

- Count rows in the `deliveries` table:
  ```sql
  SELECT COUNT(*) FROM deliveries;
  ```

### 5. Clean Up

If you need to remove the database and user, run the cleanup script:

```bash
psql -U postgres -f scripts/dropUserDatabase.sql
```

This script:
1. Drops the `ipl_database` database.
2. Drops the `ipl_user` user.

## Files Description

### Scripts
- **`createUserDatabase.sql`**: Creates a new user and database, assigning ownership to the user.
- **`dropUserDatabase.sql`**: Cleans up the user and database created.
- **`load_ipl_data.sql`**: Creates the `matches` and `deliveries` tables and imports data from the CSV files.

### Data
- **`matches.csv`**: Contains IPL match information.
- **`deliveries.csv`**: Contains IPL delivery details for each match.

### Supporting Files
- **`.gitignore`**: Ensures sensitive or unnecessary files are not tracked by Git.
- **`README.md`**: Provides instructions for setting up and running the project.

## Notes

- Ensure proper file permissions for the CSV files so that the PostgreSQL server can access them.
- If any issue arises with absolute paths, update the file paths in `load_ipl_data.sql` accordingly.

## Author
Utkarsh



