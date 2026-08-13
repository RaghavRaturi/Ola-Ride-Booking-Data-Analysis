# Ola-Ride-Booking-Data-Analysis
SQL | Power BI | Excel | Business Intelligence

End-to-end data analysis project analyzing 103k+ OLA ride bookings using SQL and power BI to uncover booking trends, cancellation patterns, revenue performance, vehicle-wise metrics, and customer/driver ratings.

---

## Project Overview
This Project analyzes **103,024 OLA ride-booking records** to answer key business questions related to :

- Booking Performance
- Successful and cancelled rides
- Vehicle-type Performance
- Customer and driver behavior
- Revenue and payment methods
- Ride distance
- Customer and driver ratings
- cancellation reasons
- Incomplete rides

The analysis was performed using SQL queries and visualized through a multi-page Power BI dashboard.
<img width="1919" height="1139" alt="image" src="https://github.com/user-attachments/assets/5be6e0b3-7794-44ab-b9e6-bede8846c30d" />
<img width="1919" height="1138" alt="image" src="https://github.com/user-attachments/assets/d396dc26-2dd9-4ee0-8ae7-cecf634e85e7" />
<img width="1919" height="1140" alt="image" src="https://github.com/user-attachments/assets/a23ff2f6-9b76-4b5e-b316-702d9184cf8d" />
<img width="1919" height="1139" alt="image" src="https://github.com/user-attachments/assets/f01ba354-3d5f-47f2-b32e-caa5e925d56b" />
<img width="1919" height="1140" alt="image" src="https://github.com/user-attachments/assets/7d0ba203-5461-40ec-b48d-9df401a4b6fc" />

## Business Objectives
the primary objectives of this project are:

1. Analyze overall ride-booking performance.
2. Identify trends in successful and cancelled bookings.
3. Compare vehicle types based on ride distance and ratings.
4. Analyze revenue by payment method and customer.
5. Understand customer and driver cancellation behavior.
6. Analyze customer and driver ratings.
7. Identify patterns that can support operational decision-making.

 ---

 ## Tools & Technologies
| tools | Purpose |
|-------|---------|
| SQL | Data queries and business analysis |
| Power BI | Interactive dashboards and visualization |
| Microsoft Excel | Data storage and initial data inspection | 


---

## Dataset

the dataset contains **103,024 booking records**.

## key columns

| column | Description |
|--------|-------------|
| Date | Booking date |
| Time | Booking time |
| Booking_ID | Unique booking identifier | 
| Booking_Status | Status of the booking |
| Customer_ID | Unique customer identifier | 
| Vehicle_Type | Type of vehicle used |
|Pickup_Location | Ride pickup location |
| Drop_Location | Ride Destination |
| V_TAT | Vehicle turnaround time |
| C_TAT | Customer turnaround time | 
| Canceled_Rides_by_Customer | Customer cancellation reason |
| Canceled_Rides_by_Driver | Driver cancellation reason | 
| Incomplete_Ride_Reason | Reason for incomplete ride |
| Booking_Value | Value of the booking |
| Payment_method | Payment method used |
| Ride_Distance | Distance travelled |
| Driver_Ratings | Rating given to the driver |
| Customer_rating | Rating associated with the customer |

---

Power BI Dashboard

The Power BI report is divided into five analytical views.

### 1. Overall

- Ride Volume Over Time
- Booking Status Breakdown
- Total Bookings
- Successful Bookings
- Overall Booking Performance 

### 2. Vehicle Type

- Top 5 Vehicle Types by Rides Distance
- Total Booking Value
- Successful Booking Value
- Average Ride Distance
- Total Distance Travelled

### 3. Revenue

- Revenue by Payment Method
- Top 5 Customers by Total Booking Value
- Ride Distance Distribution Per Day

### 4. Cancellation

- Cancelled Rides by Customer
- Cancelled Rides by Driver
- Customer cancellation reasons
- Driver cancellation reasons
- Cancellation KPIs

### 5. Ratings

- Driver Ratings by Vehicle Type
- Customer ratings by Vehicle Type
- Comparison of customer and driver ratings

---

## Key Dashboard KPIs
| KPI | Value |
|-----|-------|
| Total Bookings | 103,024 |
| Successful Bookings | 63,967 |
| cancellation Rate | 28.08% |
| Dataset Records | 103,024 |

---

# SQL Analysis
The project answers 10 business questions using SQL.
### 1. Retrieve all successful bookings

SELECT * 
FROM bookings 
WHERE Booking_Status = 'Success';

### 2. Find the average ride distance for each vehicle type

SELECT 
      Vehicle_Type,
      AVG(Ride_Distance) as avg_distance 
FROM bookings 
GROUP BY Vehicle_Type ;

### 3. Get the Total number of rides cancelled by customers

SELECT 
       COUNT(*) AS total_customer_cancellation
FROM bookings 
WHERE Booking_Status = 'cancelled by Customer';

### 4. List the top 5 customers who booked the highest number of rides

SELECT 
      Customer_ID, 
      COUNT(Booking_ID) as total_rides 
FROM bookings 
GROUP BY Customer_ID 
ORDER BY total_rides DESC 
LIMIT 5;

### 5. Get the number of rides cancelled by drivers due to personal and car-related issues

SELECT 
      COUNT(*) AS driver_cancellation_personal_reason
FROM bookings 
WHERE cancelled_Rides_by_Driver = 'Personal & Car related issue';

### 6.  Find the maximum and minimum driver ratings for Prime Sedan bookings

SELECT 
       MAX(Driver_Ratings) as max_rating, 
       MIN(Driver_Ratings) as min_rating 
FROM bookings 
WHERE Vehicle_Type = 'Prime Sedan';

### 7. Retrieve all rides where payment was made using UPI

SELECT * 
FROM bookings 
WHERE Payment_Method = 'UPI';

### 8. Find the average customer rating per vehicle type
SELECT 
      Vehicle_Type, 
      AVG(Customer_Rating) as avg_customer_rating 
FROM bookings
GROUP BY Vehicle_Type;

### 9. Calculate the total booking value of rides completed successfully
SELECT 
      SUM(Booking_Value) as total_successful_value 
FROM bookings 
WHERE Booking_Status = 'Success';
 
### 10. List all incomplete rides along with the reason
SELECT 
      Booking_ID, 
      Incomplete_Rides_Reason 
FROM bookings 
WHERE Incomplete_Rides = 'Yes';


How to use 

SQL
1. Load the OLA booking dataset into your SQL database.
2. Create a Table named Bookings.
3. Run the queries available :
4. SQL/analysis_queries.sql

Power BI
1. Open the .pbix file using Microsoft Power BI Dekstop.
2. Connect/reconnect the dataset if required.
3. Explore the five dashboard pages.
4. Use the filters and visuals to investigate booking and operational trends.





  







 
