# British Airways: Passenger Satisfaction & Operational Analytics
An executive-level Power BI case study analyzing customer sentiment, operational service metrics, and fleet performance for British Airways. This project translates raw passenger feedback into actionable, data-driven strategies for airline executives.


## 📊 Dashboard Environment Overview
The interactive dashboard uses advanced DAX measures to dynamically filter metrics while keeping the interface clean, intuitive, and visually aligned with corporate standards.
### 🛠️ Built With
* **Power BI Desktop** (Data modeling, UI/UX design, visual integration)
* **Power Query (M)** (Data cleaning, normalization, text parsing, and type handling)
* **DAX** (Dynamic metric switching, cumulative averages, and row-count filtering)
## 💡 Executive Insights & Visual Deep-Dive
### 1. Key Performance Bottlenecks
Our high-level card metrics indicate that although British Airways maintains a stable **Overall Rating of 4.39/10**, severe friction exists within the physical experience:
* **Value for Money (2.80/10)** & **Seat Comfort (2.90/10)** are trailing indicators, pointing directly to a mismatch between ticket price and physical cabin comfort.
* Conversely, **Ground Service (3.11/10)** serves as a relative operational highlight to build upon.
### 2. Seasonality & Flight Trends
The historical satisfaction analysis shows strong, recurring cyclical waves in customer sentiment:
* **September Peak:** High customer satisfaction values peaks at late summer, driven primarily by off-peak vacation travelers and lower business travel congestion.
* **March Compression:** Travel sentiment dips sharply in late Q1 due to late-winter schedule adjustments and high-density business queues.
### 3. Geographical Sentiment Clustering
Plotting the geographical coordinates of passenger feedback reveals where the volume of customer sentiment is concentrated globally:
* **European Core Hub:** Massive concentration surrounding London Heathrow (LHR) feeders.
* **Transatlantic Corridors:** Dense clusters along the East Coast of North America, highlighting BA's most critical long-haul routes.
### 4. Fleet Performance & Handling Outliers
In the raw data, low-frequency aircraft types skew performance ratings (e.g., the E170 falsely registered a perfect 10.0 score from a single review). By implementing custom filters, we eliminated this bias to show true active performance scores:
* **The Heavy Lifters:** The **Boeing 777** commands over **125 reviews** yet ranks on the lower end of satisfaction (4.1).
* **The High Performers:** The **Airbus A350** leads realistic fleet scores at **7.0**, serving as the model standard for seating configurations.
## 🧠 Advanced DAX Measures Applied
### Dynamic Canvas Context Switching
Instead of building separate charts for each rating metric, a single dynamic parameter allows stakeholders to switch the entire report canvas between rating categories using a single slicer:
```dax
Dynamic Rating =
SWITCH(
    SELECTEDVALUE('MetricSelection'[Metric Name]),
    "Cabin Staff Service", AVERAGE('ba_reviews'[cabin_staff_service]),
    "Entertainment", AVERAGE('ba_reviews'[entertainment]),
    "Food & Beverages", AVERAGE('ba_reviews'[food_beverages]),
    "Ground Service", AVERAGE('ba_reviews'[ground_service]),
    "Seat Comfort", AVERAGE('ba_reviews'[seat_comfort]),
    "Value For Money", AVERAGE('ba_reviews'[value_for_money]),
    AVERAGE('ba_reviews'[rating]) -- Default backup
)

```
### Total Reviews Count (Filtering Outliers)
This calculation serves as the foundation for the visual-level filter on fleet charts to remove single-review noise:
```dax
Total Reviews Count = COUNTROWS('ba_reviews')

```
## 🚀 Strategic Recommendations
1. **Target the Boeing 777 Fleet:** Prioritize physical cabin upgrades (improved legroom/seating) on the Boeing 777 series first, as this single fleet represents the highest volume of reviews and customer complaints.
2. **Re-evaluate Pricing Strategies:** Address the low **Value for Money (2.80)** rating by benchmarking dynamic pricing or bundling complementary premium lounge or baggage services on routes with legacy cabins.
3. **Data Integrity Standard:** Maintain a reporting threshold requiring a minimum of **5 customer reviews** before including any fleet unit in performance visualizations.


### 👤 Author
Developed and maintained by **Arushi Nigam** (July 2026).
