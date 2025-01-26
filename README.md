# Revenue-Insights-in-Hospitality


This project analyzes key performance metrics for the hospitality industry, focusing on insights derived from hotel booking data. The analysis is conducted using Power BI, with the following steps:

📂 Data Collection: Extracted data from relevant sources.

🔄 Data Transformation: Cleaned and processed data using Power Query and DAX formulas.

📊 Insight Extraction: Leveraged DAX calculations to generate meaningful business metrics
Below, we detail the DAX formulas and the corresponding insights they provide:

📈 Metrics and Insights

1️⃣ Revenue 💵

Purpose: Calculate the total revenue generated.

Formula: Revenue = SUM(fact_bookings[revenue_realized])

Table: fact_bookings

2️⃣ Total Bookings 📝

Purpose: Count the total number of bookings.

Formula: Total Bookings = COUNT(fact_bookings[booking_id])

Table: fact_bookings

3️⃣ Total Capacity 🛏️

Purpose: Calculate the total room capacity across all hotels.

Formula: Total Capacity = SUM(fact_aggregated_bookings[capacity])

Table: fact_aggregated_bookings

4️⃣ Total Successful Bookings ✅

Purpose: Sum up all successful bookings.

Formula: Total Successful Bookings = SUM(fact_aggregated_bookings[successful_bookings])

Table: fact_aggregated_bookings

5️⃣ Occupancy Percentage 📊

Purpose: Measure the proportion of rooms utilized compared to total capacity.

Formula: Occupancy % = DIVIDE([Total Successful Bookings],[Total Capacity],0)

Table: fact_aggregated_bookings

6️⃣ Average Rating ⭐

Purpose: Calculate the average customer rating.

Formula: Average Rating = AVERAGE(fact_bookings[ratings_given])

Table: fact_bookings

7️⃣ Number of Days 📅

Purpose: Determine the total number of days in the dataset.

Formula: No of days = DATEDIFF(MIN(dim_date[date]),MAX(dim_date[date]),DAY) +1

Table: dim_date

8️⃣ Total Cancelled Bookings ❌

Purpose: Identify all bookings marked as "Cancelled."

Formula: Total cancelled bookings = CALCULATE([Total Bookings],fact_bookings[booking_status]="Cancelled")

Table: fact_bookings

9️⃣ Cancellation Percentage 📉

Purpose: Calculate the proportion of bookings canceled.

Formula: Cancellation % = DIVIDE([Total cancelled bookings],[Total Bookings])

Table: fact_bookings

🔟 Total Checked Out 🏁

Purpose: Sum all "Checked Out" bookings.

Formula: Total Checked Out = CALCULATE([Total Bookings],fact_bookings[booking_status]="Checked Out")

Table: fact_bookings

1️⃣1️⃣ Total No-Show Bookings 🚫

Purpose: Identify bookings where customers neither canceled nor attended.

Formula: Total no show bookings = CALCULATE([Total Bookings],fact_bookings[booking_status]="No Show")

Table: fact_bookings

1️⃣2️⃣ No-Show Rate Percentage 📉

Purpose: Calculate the percentage of no-show bookings.

Formula: No Show rate % = DIVIDE([Total no show bookings],[Total Bookings])

Table: fact_bookings

1️⃣3️⃣ Booking Percentage by Platform 🌐

Purpose: Show each platform’s contribution to total bookings.

Formula: Booking % by Platform = DIVIDE([Total Bookings], CALCULATE([Total Bookings], ALL(fact_bookings[booking_platform])))*100

Table: fact_bookings

1️⃣4️⃣ Booking Percentage by Room Class 🏢

Purpose: Show the contribution of each room class.

Formula: Booking % by Room class = DIVIDE([Total Bookings], CALCULATE([Total Bookings], ALL(dim_rooms[room_class])))*100

Tables: fact_bookings, dim_rooms

1️⃣5️⃣ Average Daily Rate (ADR) 🏷️

Purpose: Measure average revenue per room booked.

Formula: ADR = DIVIDE([Revenue], [Total Bookings],0)

Table: fact_bookings

1️⃣6️⃣ Realization Percentage 📊

Purpose: Measure successful check-outs as a percentage of total bookings.

Formula: Realisation % = 1- ([Cancellation %]+[No Show rate %])

Table: fact_bookings

1️⃣7️⃣ Revenue per Available Room (RevPAR) 💰

Purpose: Measure revenue generated per available room.

Formula: RevPAR = DIVIDE([Revenue],[Total Capacity])

Tables: fact_bookings, fact_aggregated_bookings

1️⃣8️⃣ Daily Booked Room Nights (DBRN) 🛌

Purpose: Calculate the average number of rooms booked daily.

Formula: DBRN = DIVIDE([Total Bookings], [No of days])

Tables: fact_bookings, dim_date

1️⃣9️⃣ Daily Sellable Room Nights (DSRN) 🏠

Purpose: Calculate the average number of rooms available daily.

Formula: DSRN = DIVIDE([Total Capacity], [No of days])

Tables: fact_aggregated_bookings, dim_date

2️⃣0️⃣ Daily Utilized Room Nights (DURN) 🛌

Purpose: Calculate the average number of rooms utilized daily.

Formula: DURN = DIVIDE([Total Checked Out],[No of days])

Tables: fact_bookings, dim_date

2️⃣1️⃣ Week-over-Week (WoW) Metrics 🔄

Purpose: Calculate percentage change for key metrics week-over-week.

Formulas:

Revenue WoW Change %: Revenue WoW change % = DIVIDE(revcw,revpw,0)-1

Occupancy WoW Change %: Occupancy WoW change % = DIVIDE(revcw,revpw,0)-1

ADR WoW Change %: ADR WoW change % = DIVIDE(revcw,revpw,0)-1

RevPAR WoW Change %: Revpar WoW change % = DIVIDE(revcw,revpw,0)-1

Realization WoW Change %: Realisation WoW change % = DIVIDE(revcw,revpw,0)-1

DSRN WoW Change %: DSRN WoW change % = DIVIDE(revcw,revpw,0)-1

🎨 Visualizations:

📊 Revenue Trends: Identify trends over time.

💻 Platform Performance: Compare performance of booking platforms.

🏠 Room Utilization Metrics: Analyze occupancy, RevPAR, and ADR

✨ Conclusion

This project showcases how Power BI and DAX can transform raw booking data into actionable insights, empowering decision-making in the hospitality sector.

📁 Repository Structure

📂 Data: Contains sample datasets.

📊 Power BI File: .pbix file for the report.

📝 Documentation: Detailed explanations of metrics and methodologies.
