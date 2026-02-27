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
1️⃣ Users Table
CREATE TABLE Users (
    user_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    gender VARCHAR(10),
    city VARCHAR(100)
);
2️⃣ Trains Table
CREATE TABLE Trains (
    train_id INT PRIMARY KEY,
    train_name VARCHAR(100),
    source VARCHAR(100),
    destination VARCHAR(100),
    distance_km INT
);
3️⃣ Bookings Table
CREATE TABLE Bookings (
    booking_id INT PRIMARY KEY,
    user_id INT,
    train_id INT,
    journey_date DATE,
    booking_date DATE,
    class VARCHAR(20),
    fare DECIMAL(10,2),
    status VARCHAR(20), -- Confirmed / Waiting / Cancelled
    FOREIGN KEY (user_id) REFERENCES Users(user_id),
    FOREIGN KEY (train_id) REFERENCES Trains(train_id)
);
📊 Step 2: Important SQL Queries (For Dashboard)
🔹 Total Revenue
SELECT SUM(fare) AS total_revenue
FROM Bookings
WHERE status = 'Confirmed';
🔹 Most Popular Route
SELECT t.source, t.destination, COUNT(*) AS total_bookings
FROM Bookings b
JOIN Trains t ON b.train_id = t.train_id
GROUP BY t.source, t.destination
ORDER BY total_bookings DESC;
🔹 Booking Trend Monthly
SELECT MONTH(booking_date) AS month,
       COUNT(*) AS total_bookings
FROM Bookings
GROUP BY MONTH(booking_date);
🔹 Cancellation Rate
SELECT 
  (SUM(CASE WHEN status='Cancelled' THEN 1 ELSE 0 END)*100.0 / COUNT(*)) 
  AS cancellation_percentage
FROM Bookings;
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