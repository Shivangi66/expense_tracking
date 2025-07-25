# Expense Tracking Application

A full-stack expense tracking application built with FastAPI backend and Streamlit frontend, using Oracle database for data persistence.

## Features

- **Daily Expense Management**: Add, update, and view expenses for specific dates
- **Category-based Tracking**: Organize expenses by categories (Food, Rent, Shopping, Travel, Celebration, Other)
- **Analytics Dashboard**: View expense breakdowns by category with percentage calculations
- **Monthly Analysis**: Track and visualize expenses by month
- **RESTful API**: Backend API for expense operations and analytics

## Tech Stack

- **Backend**: FastAPI, Python 3.12
- **Frontend**: Streamlit
- **Database**: Oracle Database
- **Data Visualization**: Altair, Pandas
- **Testing**: Pytest
- **Logging**: Custom logging setup

## Project Structure

```
expense_tracking/
├── backend/
│   ├── db_helper.py          # Database operations
│   ├── server.py             # FastAPI server
│   ├── setup_logger.py       # Logging configuration
│   └── expense_app.log       # Application logs
├── frontend/
│   ├── app.py                # Main Streamlit application
│   ├── CRUD_expenses.py      # Daily expense management UI
│   ├── analytics_ui.py       # Category analytics UI
│   └── analysis_by_month_ui.py # Monthly analysis UI
├── tests/
│   └── test_db_helper.py     # Unit tests for database operations
├── requirements.txt          # Python dependencies
└── README.md
```

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd expense_tracking
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Database Setup**
   - Ensure you have access to an Oracle database
   - Update database connection details in `backend/db_helper.py`
   - Create the required `expenses` table with the following schema:
   ```sql
   CREATE TABLE expenses (
       id NUMBER GENERATED ALWAYS AS IDENTITY
       expense_date DATE,
       amount NUMBER,
       category VARCHAR2(100),
       notes VARCHAR2(500)
   );
   ```

## Usage

### Starting the Backend Server

```bash
cd backend
uvicorn server:app --host 127.0.0.1 --port 8088
```

The API will be available at `http://127.0.0.1:8088`

### Starting the Frontend Application

```bash
cd frontend
streamlit run app.py
```

The web application will open in your browser at `http://localhost:8501`

## API Endpoints

### Expenses
- `GET /expenses/{expense_date}` - Fetch expenses for a specific date
- `POST /expenses/{expense_date}` - Add/update expenses for a specific date

### Analytics
- `POST /analytics/` - Get expense summary by category for a date range
- `GET /analytics_by_month/` - Get monthly expense breakdown

## Testing

Run the test suite using pytest:

```bash
pytest tests/
```

## Features Overview

### 📅 Daily Expenses
- Add up to 5 expenses per day
- Select from predefined categories
- Add notes for each expense
- Update existing expenses

### 📊 Analytics
- View expense breakdown by category
- Percentage calculation of expenses
- Custom date range selection
- Interactive bar charts

### 📈 Analytics By Month
- Monthly expense visualization
- Automatic data aggregation by month
- Interactive charts and data tables

## Database Operations

The application supports the following database operations:
- [`fetch_expenses_for_date`](backend/db_helper.py) - Retrieve expenses for a specific date
- [`insert_expense`](backend/db_helper.py) - Add new expense record
- [`delete_expenses_for_date`](backend/db_helper.py) - Remove all expenses for a date
- [`fetch_expense_summary`](backend/db_helper.py) - Get category-wise expense summary
- [`fetch_expense_summary_by_month`](backend/db_helper.py) - Get monthly expense totals

## Logging

The application includes comprehensive logging:
- Function call logging with arguments
- Database operation logging
- Error tracking and debugging information
- Logs stored in `backend/expense_app.log`

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Run the test suite
6. Submit a pull request

## Dependencies

See [requirements.txt](requirements.txt) for a complete list of dependencies including:
- FastAPI for the backend API
- Streamlit for the frontend
- oracledb for database connectivity
- pandas and altair for data processing and visualization
- pytest for testing

## Support

For issues and questions, please create an issue in the repository.