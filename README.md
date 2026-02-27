🚆 IRCTC Ticket Booking Dashboard Project

(Reference system: Indian Railway Catering and Tourism Corporation)

🎯 Project Objective

Build a dashboard to analyze:

📅 Ticket bookings over time

💺 Seat class preference

🌍 Most popular routes

💰 Revenue trends

❌ Cancellation patterns

🧑‍🤝‍🧑 Passenger demographics

This is a real-world DBMS + Excel + Power BI integration project.

🗂️ Step 1: Database Design (DBMS Part)

Use MySQL / PostgreSQL

📌 Tables Design
1️⃣ Users Table <br>
CREATE TABLE Users (<br>
    user_id INT PRIMARY KEY,<br>
    name VARCHAR(100),<br>
    age INT,<br>
    gender VARCHAR(10),<br>
    city VARCHAR(100)<br>
);<br>

2️⃣ Trains Table<br>
CREATE TABLE Trains (<br>
    train_id INT PRIMARY KEY,<br>
    train_name VARCHAR(100),<br>
    source VARCHAR(100),<br>
    destination VARCHAR(100),<br>
    distance_km INT<br>
);<br>

3️⃣ Bookings Table<br>
CREATE TABLE Bookings (<br>
    booking_id INT PRIMARY KEY,<br>
    user_id INT,<br>
    train_id INT,<br>
    journey_date DATE,<br>
    booking_date DATE,<br>
    class VARCHAR(20),<br>
    fare DECIMAL(10,2),<br>
    status VARCHAR(20), -- Confirmed / Waiting / Cancelled<br>
    FOREIGN KEY (user_id) REFERENCES Users(user_id),<br>
    FOREIGN KEY (train_id) REFERENCES Trains(train_id)<br>
);<br>

📊 Step 2: Important SQL Queries (For Dashboard)<br>
🔹 Total Revenue<br>
SELECT SUM(fare) AS total_revenue<br>
FROM Bookings<br>
WHERE status = 'Confirmed';<br>
🔹 Most Popular Route<br>
SELECT t.source, t.destination, COUNT(*) AS total_bookings<br>
FROM Bookings b<br>
JOIN Trains t ON b.train_id = t.train_id<br>
GROUP BY t.source, t.destination<br>
ORDER BY total_bookings DESC;<br>

🔹 Booking Trend Monthly<br>
SELECT MONTH(booking_date) AS month,<br>
       COUNT(*) AS total_bookings<br>
FROM Bookings<br>
GROUP BY MONTH(booking_date);<br>

🔹 Cancellation Rate<br>
SELECT <br>
  (SUM(CASE WHEN status='Cancelled' THEN 1 ELSE 0 END)*100.0 / COUNT(*)) <br>
  AS cancellation_percentage<br>
FROM Bookings;<br>
📈 Step 3: Excel Part

After exporting SQL data to Excel:

Use:

Pivot Tables

Slicers

Charts:

Line chart → Booking trend

Bar chart → Class preference

Pie chart → Gender distribution

Column chart → Revenue per route

📊 Step 4: Power BI Dashboard Design
📌 Data Model

Import data from MySQL

Create relationships:

Users ↔ Bookings

Trains ↔ Bookings

📌 DAX Measures
<br>
Total Revenue
Total Revenue = 
CALCULATE(SUM(Bookings[fare]), Bookings[status] = "Confirmed")
Total Bookings
Total Bookings = COUNT(Bookings[booking_id])
Cancellation %
Cancellation % = 
DIVIDE(
    CALCULATE(COUNT(Bookings[booking_id]), Bookings[status] = "Cancelled"),
    COUNT(Bookings[booking_id])
)
<br>
🎨 Suggested Dashboard Layout
🔷 Top KPIs

Total Revenue 💰

Total Bookings 🎫

Cancellation % ❌

Avg Fare 💵

🔷 Middle Section

📅 Booking Trend (Line Chart)

🛤️ Top Routes (Bar Chart)

🔷 Bottom Section

💺 Class Distribution

👩‍🦰 Gender Distribution

🌆 Top Cities by Booking

🚀 Advanced Features (Make It “Dashing” 🔥)

Add:

📍 Map visualization (City-wise bookings)

📊 Drill-through to route-level analysis

📅 Date slicer

🎛️ Class filter

📉 Revenue forecasting (Power BI analytics feature)

💡 Real-World Use Case

Such dashboards help:

Railway authorities optimize routes

Predict peak seasons

Manage waiting lists

Improve pricing strategy

Reduce cancellations

🧠 Why This Is Good For You (Data Scientist Path)

Since you want to become a Data Scientist:

This project shows:

✔️ DBMS knowledge

✔️ SQL joins & aggregation

✔️ Data cleaning

✔️ Visualization skills

✔️ Business insight generation

Very strong resume project 👍

If you want, I can next give:

🔥 Sample dataset (insert queries)

📊 Complete Power BI dashboard structure with screenshots explanation

🧠 Add Machine Learning (Demand Prediction Model)

Which level do you want? Basic / Advanced / With ML? 🚀