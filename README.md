# ☀️ Solar Power Performance Prediction Pipeline

This is an end-to-end data project that builds a complete pipeline to predict the power output of a solar PV array. The project ingests raw sensor data, uses a Python-based machine learning model to make predictions, loads the results into a SQL database, and visualizes the entire system in a Power BI dashboard.

---

## 📊 Power BI Dashboard

**Note:** A live web link requires a work/school account. To view the dashboard:

1.  **Download the `.pbix` file** from this repository [by clicking here](./Solar_Dashboard.pbix).
2.  **Open the file** using the free [Power BI Desktop](https://powerbi.microsoft.com/desktop/) application.
3.  The dashboard will connect to the `cleaned_generation_data` table for its visuals.

<img width="1167" height="609" alt="Screenshot 2025-11-13 163344" src="https://github.com/user-attachments/assets/dbfe2966-e9a3-4afe-87a7-6391e00d6a6e" />


---

## 🏛️ Project Architecture

This project follows a complete ETL-style (Extract, Transform, Load) and modeling workflow.

1.  **Extract & Transform (Python):** The raw `Generation_data.csv` is loaded into a **Jupyter Notebook**. Using **Pandas**, the data is cleaned, column names are standardized, and exploratory data analysis (EDA) is performed.
2.  **Model (Python):** A **LightGBM (LGBM) Regressor** is trained on the cleaned sensor data to predict the `ac_power` output. The model is trained and evaluated in the notebook.
3.  **Load (SQL):** The complete cleaned DataFrame, the test set predictions, and the model's feature importances are all loaded into a **PostgreSQL** database using **SQLAlchemy**.
4.  **Visualize (Power BI):** **Power BI Desktop** connects directly to the PostgreSQL database to build an interactive dashboard. This dashboard analyzes model performance, visualizes feature importances, and explores the raw data.

---

## 💻 Tech Stack

* **Data Analysis & Transformation:** Python, Pandas, NumPy
* **Machine Learning:** Scikit-learn, LightGBM
* **Database:** PostgreSQL
* **DB Connection:** SQLAlchemy, psycopg2
* **Visualization:** Power BI Desktop
* **IDE:** Jupyter Lab

---

## 📈 Key Results

The machine learning model performed exceptionally well, proving the strong correlation between sensor readings and power output.

* **R-Squared:** **0.98** (The model explains 98% of the variance in power output)
* **RMSE:** **11,51 kiloWatts** (The model's average prediction error)
* **Top Feature:** `irradiance` was identified as the most important predictor of power.

---

## 🚀 How to Run This Project

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/EngEleLuiz/Solar-Generation-Forecasting-Pipeline]
    ```
2.  **Set up the Environment:**
    * Install the required Python libraries:
        ```bash
        pip install pandas numpy scikit-learn lightgbm sqlalchemy psycopg2-binary jupyterlab
        ```
    * Install and run a local [PostgreSQL server](https://www.postgresql.org/download/).
    * Create a new database in PostgreSQL (e.g., `solar_db`).
3.  **Run the Pipeline:**
    * Open the Jupyter Notebook `Solar_Performance_Prediction_Pipeline.ipynb`.
    * Update the database connection string in **Cell 21** with your PostgreSQL username, password, and database name.
    * Run all cells in the notebook (`Kernel > Restart & Run All Cells`). This will train the model and populate your PostgreSQL database.
4.  **View the Dashboard:**
    * Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
    * Open the `Solar_Dashboard.pbix` file.
    * If prompted, click "Refresh" and ensure it can connect to your local PostgreSQL server.
