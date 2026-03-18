PROJECT TITLE :  Google Play Store Data 

Name : Shubham Thakur
Domain : Data Analytics
Project Type: Internship Project – ElevanceSkills

PROJECT DESCRIPTION :
This project analyzes the Google Play Store dataset using Python and Plotly.
It includes multiple interactive visualizations to understand app performance,
ratings, installs, revenue trends, and category insights.

TOOLS & LIBRARIES:
The project was built using:

Python
Pandas
NumPy
Plotly
NLTK
Datetime
Pytz

DATASET INFORMATION:
Two dataset were given 
1. Play Store Data.csv
2. User Review.csv

 DATASET USED :
Two datasets were used in this project:
1. Play Store  Dataset:
Contains information about Android applications such as:
1. App Name
2. Category
3. Rating
4. Reviews
5. Size
6. Installs
7. Price
8. Android Version
9. Last Updated

2️. User Reviews Dataset:
Contains user feedback for apps including:
1. Translated Reviews
2. Sentiment
3. Sentiment Polarity
4. Sentiment Subjectivity

DATA CLEANING STEPS :
The Following preprocessing steps were performed:
Handlig Missing Value:
1. Removed rows where Rating was missing.
2. Filled missing values using mode.
3. Removed duplicate records .

DATA TYPE CONVERSION :
Converted columns into appropriate formats:
1. Installs - Numeric
2. Price - Numeric
3. Reviews - Numeric
4. Last Updated - Datetime

EXAMPLE TRANSFORMATION:
10,000+ - 10000
$4.99 - 4.99

DATA TRANSFORMATION :
Several transformatoin were applied to prepare the data :
1. App Size Conversion :
Converted app size from kb/mb format nothing.

2. Log Transformation :
Logarithmic transformation applied to reduce skewness :
1. Log Installs
2. Log Reviews 
Log_Installs = log1p(Installs)
Log_Reviews = log1p(Reviews)

3. Rating group Feature :
Apps were catrgorized based on rating :
| Rating | Category      |
| ------ | ------------- |
| ≥ 4    | Top Rated App |
| ≥ 3    | Above Average |
| ≥ 2    | Average       |
| < 2    | Below Average |

4. Revenue Calculation
Revenue was estimated using:
Revenue = Installs × Price

ADDITIONAL FEATURE ENGINEERING:
Country Column :
A synthetic Country column was generated to simulate global app distribution across:
United States', 'India', 'Brazil', 'Russia', 'Japan', 'Germany', 'United Kingdom', 'France', 'Italy', 'Canada', 'Australia', 'Spain', 'Mexico', 'Netherlands', 'South Korea', 'Turkey', 'Saudi Arabia', 'Indonesia', 'Sweden', 'Switzerland'.
This allowed country-level analysis in dashboards.

SENTIMENT ANALYSIS :
User reviews were analyzed using VADER Sentiment Analysis (NLTK).
Sentiment scores include:
1. Positive
2. Negative
3. Neutral
4. Compound score
Example:
Sentiment_Score = polarity_scores(review)['compound']
Range:
-1 → Very Negative
+1 → Very Positive

VISUALIZATION CREATED :
The project includes several interactive dashboards usng Plotly.

Task 1 - Bubble Chart-– Relationship between App Size and Rating :

This visualization analyzes the relationship between app size in MB and user ratings using a bubble chart. The dataset is filtered to focus only on high-quality and popular applications from selected categories.

Filters Applied:

The following conditions were applied before creating the visualization:
1. Rating greater than 3.5
2. Reviews greater than 500
3. Installs greater than 50,000
4. App name should not contain the letter "S"
5. Sentiment Subjectivity greater than 0.5 
6. Categories limited to: Game,Beauty,Business,Comic,Communication,Dating,Entertainment,Social,Events.
Additionally, some category names were translated into different languages to demonstrate multilingual data handling.

Visuliaztion Details:
X-axis : App Size
Y-axis : App Rating
Bubble Size : Number of Installs
Color : App Category
The bubble chart is displayed only between 5 PM and 7 PM (IST) using a time-based condition implemented in the code.

Key Insights :

1. Positive Trend at Higher Sizes: There is a noticeable "step-up" in ratings for larger apps. Most apps with a size over 40 units maintain a rating above 4.3. This suggests that larger apps (which may have more features or better assets) generally maintain higher quality scores.
2. Volatility in Smaller Apps: Apps in the 0–20 size range show the highest variance. Ratings here fluctuate wildly from as low as 3.7 to as high as 4.6.
3. Rating "Floors": Most of the data points are clustered above the 4.2 rating line, indicating that this filtered dataset likely focuses on relatively successful apps.

CATEGORY-SPECIFIC OBSERVATION :
1. Dominance of "GAME": The pinkish-mauve dots (GAME) are the most prominent in the 40–80 size range. They seem to cluster around the 4.5 rating, suggesting that games are typically larger but also well-received.
2. The "ENTERTAINMENT" Outlier: There is a distinct green dot (ENTERTAINMENT) positioned at approximately Size 25 with a Rating of 4.2.
3. The High-Rating Outlier: A single small app (near Size 22) has a peak rating of approximately 4.7. This is an outlier compared to the rest of the smaller apps.
4. Lower-Tier Cluster: A small cluster of very small apps (Size < 10) sits at the bottom left with ratings around 3.7–3.8.

Task 2: Choropleth Map – Global Installs by App Category :

This visualization uses a choropleth map to analyze the global distribution of app installs across different countries and categories.

Filters Applied :

Before creating the visualization, the dataset was filtered with the following conditions:
1. Categories starting with the letters A, C, G, and S were removed.
2. The top 5 categories with the highest total installs were selected.
3. Installs were aggregated by Country and Category.

To make the visualization easier to interpret, installs were divided into two groups:
Above 1M installs
Below 1M installs(According to data there are no Installs under 1M)

Visualization Details:

1. Map Type: Choropleth Map
2. Location: Country
3. Color: Install category (Above 1M or Below 1M)
4. Hover Information: App Category and Total Installs
5. Countries with installs greater than 1 million are highlighted in blue, while those with lower installs are shown in light gray.
6. The map visualization is displayed only between 6 PM and 8 PM (IST) using a time-based condition in the code.

Key Insights:

1. A small number of countries contribute to very high install counts, indicating strong mobile app adoption in those regions.
2. The top 5 categories dominate global installs, suggesting these categories have the highest demand among users.
3. Countries with installs above 1 million are visually highlighted, making it easier to identify high-engagement regions.
4. This visualization helps identify geographical trends in app popularity across categories.

Chart Analysis :

1. The installs Above 1M are in red are concentrated in major tech consuming markets.such as:
Nort America(USA,Canada),Brazile,Russia,India,Indonesia and Austrelia.
2. Most of Africa and significant portion os Southest Asia and
South America are not highlighted. This suggests either a lack of data or those regions or that the specific app category hasn't hit the 1M milstone there yet.
3. Western and Northern Europe show high engagement,while parts of Eastern Europ (excluding Russia) appear below the threshold or unrepresented.
4. The gray areas (like China, Mexico, or the Middle East) represent massive untapped potential if the categories being filtered have high demand but low current penetration.

Task 3 : Time Series Line Chart – Monthly Installs Trend by Category :

This visualization uses a time series line chart to analyze the growth and seasonal trends of app installs over several months, segmented by specific filtered categories.

Filters applied :

Before creating the visualization, the dataset was strictly filtered to isolate high-quality  data:
1. Only apps with more than 500 reviews were included.
2. Apps starting with the letters X, Y, or Z were removed.
3. Any app containing the letter "S" (case-insensitive) was excluded to filter out major social media or specific brand names.
4. Only categories starting with E, C, or B were analyzed
5. To support a global team, specific categories were translated:
BEAUTY - सौंदर्य (Hindi),BUSINESS - வணிகம் (Tamil),DATING - Verabredung (German)

Visualization Details:

Chart Type: Time Series Line Chart.
X-Axis: Month (derived from the Last Updated column).
Y-Axis: Total Installs.
Color Segmentation: App Category (using translated names).
Special Highlight: Shaded areas under the curves indicate significant growth periods where installs increased by more than 20% month-over-month.

Key Insights:

1.  The chart shows a massive, exponential spike in installs across almost all filtered categories starting in early 2018. This suggests a major market expansion or a shift in how data was recorded during that period.

2.  The COMMUNICATION category (red line) is the clear market leader, reaching a staggering peak of over 120 Billion installs, significantly outperforming all other segments.

3.  The category Business shows consistent visibility, indicating that translated/localized business apps maintain a steady presence even when the broader market fluctuates.

4.  The shaded regions (seen clearly in the 2018 surge) highlight that the growth wasn't just large in volume, but rapid in pace (exceeding the 20% growth threshold).

Chart Analysis:

1.  From 2015 to late 2017, installs remained relatively flat and low. The sudden vertical rise in 2018 indicates a "hyper-growth" phase for the apps that passed the "No S" and "No XYZ" filters.

2.  While Communication leads, Education and Books & Reference (blue and green lines) show smaller but mirrored growth patterns, suggesting that the factors driving the 2018 surge were universal across these sectors.

3.  By excluding apps with the letter "S," we are likely seeing the rise of alternative communication tools and business platforms that are not dominated by the typical "Social" (S) giants.

4.  The sharp drop-off at the very end of the 2018 period in some traces suggests a market correction or a seasonal dip after a major peak.

Task 4 : Stacked Area Chart–Cumulative Installs Over Time by Category :

This visualization uses a stacked area chart to demonstrate the growth of total app installs, showing how each specific category contributes to the overall market volume over time.

Filters Applied:

To focus on high-quality, professional-grade applications, the dataset was filtered with the following strict criteria:

1. Only apps with an average Rating of 4.2 or higher and more than 
1,000 reviews were included.
2. App names containing any numerical digits were excluded to filter out "lite" versions or sequels
3. Only apps with a file size between 20 MB and 80 MB were analyzed, targeting mid-to-high-tier applications.
4. Includes only categories starting with the letters “T” or “P.”
5. The legend was localized for international stakeholders:
TRAVEL_AND_LOCAL - Voyage et Local (French),PRODUCTIVITY - Productividad (Spanish),PHOTOGRAPHY -  (Japanese)

Visualization Details:

1. Chart Type: Stacked Area Chart.
2. X-Axis: Month (Time series).
3. Y-Axis: Cumulative Installs (showing the running total).
4. Dynamic Highlighting: Color intensity increases for any month where a category's installs grew by more than 25% month-over-month.
5. Time Restriction: This visualization is programmed to be active and visible only between 4 PM IST and 6 PM IST.

Key Insights:

1. Similar to previous tasks, the data shows a massive vertical "breakout" in July 2018. Prior to this, cumulative growth was negligible, suggesting a sudden and massive influx of users or a significant update in data reporting for these categories.

2. The green band representing Productividad (Productivity) occupies the largest area of the stack. This indicates that productivity apps are the primary drivers of total volume within this filtered group.

3. The Photography category shows a sharp spike at the very end of the timeline, indicating it is currently the fastest-growing segment among the selected categories.

4.  The mirrored growth across Voyage et Local and Productividad suggests that the user base for these categories expanded simultaneously, likely due to a general increase in mobile tool adoption in mid-2018.

Chart Analysis:

1.  The chart remains almost flat until May/June 2018, where it begins a steep climb. By July 2018, the total volume crosses 120 Billion installs. This "hockey stick" growth is a key characteristic of this specific filtered dataset.

2. Because the chart is stacked, the top-most line (Photography) represents the aggregate total of all three categories, providing a clear view of the total "T" and "P" market size.

3.  The increased color intensity during the July 2018 surge visually confirms that the growth was not just large in volume, but hit the >25% month-over-month trigger, marking it as an "extraordinary" growth event.

4. By excluding apps with numbers in the name, the chart effectively captures "Original" brands, showing that established, non-sequel apps are capable of massive scale.

Task 5: Grouped Bar Chart – Average Rating and Total Reviews by Category:

This visualization utilizes a grouped bar chart to perform a dual-metric comparison, evaluating both user satisfaction (Average Rating) and user engagement volume (Total Reviews) across the most popular app categories.

Filters Applied:

To ensure the data reflects high-performing, substantial apps updated during the start of the year, the following criteria were applied:
1. Only apps with a Rating of 4.0 or higher and a file size of at least 10 MB were included.
2. The analysis is strictly limited to apps that received their last update in the month of January.
3. The data was filtered to show only the Top 10 categories based on total Installs.
4. Total review counts were divided by 1,000,000 (Millions) to allow for a readable comparison against the 0–5 rating scale on a single Y-axis.

Visualization Details:

1. Chart Type: Grouped Bar Chart.
2. X-Axis: App Category.
3. Y-Axis: Numerical value representing both the Average Rating (out of 5) and Total Reviews (in Millions).
4. Color Coding: * Blue: Average Rating.
5. Orange/Coral: Total Reviews (Millions).
6. Time Restriction: This chart is dynamically programmed to be visible on the dashboard only between 3 PM IST and 5 PM IST.

Key Insights:

1. The FAMILY category stands out as the absolute leader in user engagement. With reviews nearing 9 Million, it significantly outpaces other top categories, indicating a highly active and vocal user base.

2. While ART_AND_DESIGN has a very high average rating (over 4.0), its review volume is the lowest among the three visible categories. This suggests that while users are highly satisfied, the category has a smaller, more niche audience compared to "Family."

3. All top categories maintain an average rating between 4.0 and 4.5. This proves that the "Top 10 by Installs" are not just popular by luck, but consistently deliver a high-quality user experience that meets the 4.0 threshold.

4. The PHOTOGRAPHY category shows a healthy balance—retaining a strong 4.0 rating while generating a significant amount of feedback (approx. 1 Million reviews).

Chart Analysis:

1. There is a massive disparity in engagement between "Family" and other categories. The "Family" category's orange bar is roughly 8-9 times taller than that of "Photography," highlighting where the bulk of user interaction is concentrated.

2. Because this data represents apps updated in January, the high ratings across the board suggest that "New Year" updates for these top categories were generally well-received by the community.

3. By using a grouped bar format, we can see that even though "Art and Design" has a slightly higher rating than "Photography," its lack of a visible orange bar (due to low review volume) identifies it as a lower-engagement segment.

4. For developers, the "Family" category offers the highest visibility and feedback loop, while "Art and Design" represents a high-satisfaction "Blue Ocean" with less competition in terms of raw review volume.

Task 6: Dual-Axis Chart – Average Installs vs. Revenue :

This visualization utilizes a dual-axis approach (combining a bar chart and a line-scatter plot) to analyze the relationship between popularity (Installs) and financial performance (Revenue) for different business models.

Filters Applied:

To ensure the analysis focuses on established, mainstream apps with broad compatibility, the dataset was refined using these specific constraints:
1. Only apps with at least 10,000 installs and a total revenue of 
$10,000 or more were included.
2. Must be higher than 4.0 to ensure modern compatibility.
3. Must be greater than 15 MB.
4. Filtered exclusively for apps rated "Everyone."
5. App names were restricted to a maximum length of 30 characters (including spaces/symbols) to focus on concise branding.
6. The comparison is limited to the Top 3 categories based on total install volume.

Visualization Details:

1. Chart Type: Dual-Axis (Grouped Bar + Line with Markers).
2. X -Axis: App Type (Free vs. Paid).
3. Primary Y-Axis (Left): Average Installs (represented by the Blue Bar).
4. Secondary Y-Axis (Right): Total Revenue in USD (represented by the Red Line).
5. Time Restriction: This visualization is dynamically programmed to be visible on the dashboard only between 1 PM IST and 2 PM IST.

Key Insights:

1. In the provided chart, the Paid category shows an average install count of approximately 620k. Interestingly, while the volume is high for this specific filtered group, the revenue marker (red dot) sits around the $121.36M mark.

2.  Since the filter is set to "Everyone," these results indicate that family-friendly, non-complex apps (under 30 characters in name) are highly effective at generating both high installs and significant revenue when they cross the $10k threshold.

3.  The right-hand Y-axis is extremely granular (ranging only from 121.359M to 121.360M). This suggests that within this specific filtered subset of the Top 3 categories, the revenue generated is remarkably consistent across the apps that qualify.

4.  The chart highlights that "Paid" apps in the top categories can achieve significant scale (over half a million installs on average) while maintaining high-tier revenue, proving that users are willing to pay upfront for quality "Everyone-rated" content.

Chart Analysis:
1. The presence of only "Paid" in the visual output (or a heavy focus on it) suggests that after applying the filter for Revenue >= $10,000, the Paid apps in the Top 3 categories significantly outperformed the Free apps in that specific financial metric.

2. By limiting the app name length, the data likely excludes long, keyword-stuffed titles, focusing instead on "Brand-focused" apps. The high average installs (620k) show that short, concise names do not hinder discoverability.

3. The Revenue is concentrated at a very high level ($121.36M). This indicates that the apps passing all these filters (Size > 15M, Android > 4.0, Everyone) are "Heavy Hitters" in the marketplace.

4. The exclusion of apps with Android versions below 4.0 ensures that the revenue and install trends are not being skewed by legacy or "zombie" apps that are no longer supported by the majority of users.
