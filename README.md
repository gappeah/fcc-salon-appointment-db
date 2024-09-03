# Salon Appointment Scheduler

This project is part of the FreeCodeCamp Relational Database certification. The objective was to build a database that stores information about services, customers, and appointments in a salon and create a Bash script that interacts with this database to manage and schedule appointments.

## Project Structure

- **Database**: The database is managed using PostgreSQL.
- **Script**: A Bash script (`salon.sh`) was created to interact with the database.

### Files

- `salon.sql`: Contains SQL commands to create the database, including the necessary tables and relationships to store the services, customers, and appointments.
- `salon.sh`: A Bash script to manage and schedule appointments by interacting with the database based on user input.

## Database Schema
![diagram-export-03-09-2024-18_29_49](https://github.com/user-attachments/assets/1e163831-ec31-4cfe-b8fd-7fa87a72328b)


The database consists of the following tables:

### `services` Table

| Column Name    | Data Type | Constraints      |
| -------------- | --------- | ---------------- |
| `service_id`   | SERIAL    | PRIMARY KEY      |
| `name`         | VARCHAR   | UNIQUE, NOT NULL |

### `customers` Table

| Column Name    | Data Type | Constraints      |
| -------------- | --------- | ---------------- |
| `customer_id`  | SERIAL    | PRIMARY KEY      |
| `phone`        | VARCHAR   | UNIQUE, NOT NULL |
| `name`         | VARCHAR   | NOT NULL         |

### `appointments` Table

| Column Name    | Data Type | Constraints                           |
| -------------- | --------- | ------------------------------------- |
| `appointment_id`| SERIAL   | PRIMARY KEY                           |
| `customer_id`  | INTEGER   | REFERENCES `customers(customer_id)`   |
| `service_id`   | INTEGER   | REFERENCES `services(service_id)`      |
| `time`         | TIMESTAMP | NOT NULL                              |

## Usage

### Prerequisites

- **PostgreSQL**: Ensure PostgreSQL is installed and running on your machine. Connect to the database using:

  ```bash
  psql --username=freecodecamp --dbname=salon
  ```

- **Database Setup**: The database should be created and populated using the provided `salon.sql` file.

### Running the Script

The `salon.sh` script can be run from the command line:

```bash
./salon.sh
```

- **Service Selection**: The script will display a list of available services for the user to choose from.
- **Customer Details**: The user will be prompted to enter their phone number. If the phone number is not found in the database, the user will be asked to provide their name.
- **Appointment Scheduling**: The user will then be asked to provide a preferred time for the appointment.
- **Confirmation**: The script will confirm the appointment details with the user.

### Example Usage

```bash
~~~~~ MY SALON ~~~~~

Welcome to My Salon, how can I help you?

1) Haircut
2) Manicure
3) Pedicure

# Select a service
1

# Enter phone number
555-1234

# If new customer
What's your name?
John Doe

# Enter preferred time
2:00 PM

# Confirmation
I have put you down for a Haircut at 2:00 PM, John Doe.
```

### Error Handling

- If an invalid service number is entered, the script will prompt: `That is not a valid number.`
- If no available services are found, the script will prompt: `I could not find that service. What would you like today?`

## Project Completion

### Fixing the Database

The database was set up and refined to meet the project requirements:

1. The `services` table stores available salon services.
2. The `customers` table stores customer information, including unique phone numbers.
3. The `appointments` table stores scheduled appointments, linking services and customers.

### Bash Script

The `salon.sh` script was developed to manage and schedule salon appointments by interacting with the PostgreSQL database. 

## Installation

1. Clone this repository.
2. Set up the database:
   - Log in to PostgreSQL:
     ```bash
     psql --username=freecodecamp --dbname=postgres
     ```
   - Run the SQL commands in `salon.sql` to create and populate the database:
     ```sql
     \i salon.sql
     ```
3. Make sure the `salon.sh` script has execution permissions:
   ```bash
   chmod +x salon.sh
   ```

4. Run the script as described above.
