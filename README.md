# 📊 Introductory SQL: Analyzing Mental Health Data
![Project header](https://github.com/user-attachments/assets/194a6766-dbaf-4e70-8ff0-1e7a239ba1c0)


*Practicing basic SQL concepts to explore and analyze mental health datasets*

## 📖 Project Motivation

Understanding how to interact with databases that contain a variety of tables containing data is a necessity for anyone in the data field, especially those aspiring to creeate data pipelines in the future like I do. Thus, I decided to embark on understanding and mastering Structured Querying Language (SQL). This project was done as a practice of basic SQL keywords to master how they are used and when. 

Mental health is a critical global issue whose severity and number of cases has been rising significatnly. Using data to uncover patterns can help inform policies and interventions. This introductory project allowed me to apply newly learned concepts to a real-world dataset, building confidence in querying relational databases.

In my learning path, I started with the basics of relational databases and progressed to simple queries, filtering, and aggregation—each unit building on the previous to create a solid foundation for more advanced SQL techniques.

## 🎯 Objective

Learn and apply introductory SQL concepts to analyze a mental health dataset, including understanding relational structures, selecting data, filtering results, and deriving basic insights. The project focuses on explaining key SQL keywords (e.g., SELECT, FROM) and why they are used, while showing how I built on each unit's objectives through exercises.

This project was done to assess whether studying abroad can affect mental health. This was done to confirm whether international students have a higher risk of mental health difficulties than the general population and that social connectedness and acculturative stress are predictors of depression. To do this, the students data collected in 2018 was explored and analyzed using PostgreSQL. 

## 📂 Datasets & Schema

- Mental health dataset In the DataCamp Site. 
- Schema overview: Tables with columns for IDs, dates, scores, categories, etc.
<img width="1167" height="731" alt="Data schema 1" src="https://github.com/user-attachments/assets/2340dd73-03bf-4c9e-a202-db0910bddc26" />

<img width="1167" height="735" alt="Data schema 2" src="https://github.com/user-attachments/assets/8520ad56-a234-4118-896f-46fb8f5b4369" />

## 🛠️ Tools & Techniques

- SQL (PostgreSQL)
- Online query editor (DataCamp platform for practice)
- Key concepts: Relational databases, SELECT, FROM, WHERE, ORDER BY, LIMIT, basic aggregations (COUNT, AVG)

## 🔄 Key Units & Learnings

### 1. Introduction to Relational Databases

**What I Learned:** Relational databases organize data into tables with rows (records) and columns (attributes), connected by keys (primary/foreign) to reduce redundancy and ensure integrity. This structure allows efficient querying and relationships between datasets, like linking patient surveys to demographic info.

**Why It Matters:** Understanding this foundation is crucial for any data role, as most real-world data is stored in relational systems (e.g., SQL databases) rather than flat files like Excel.

**How I Applied It:** Reviewed schema diagrams to identify tables and relationships in the mental health dataset, preparing for queries.

### 2. Basic Querying with SELECT and FROM

**What I Learned:** 
- **SELECT**: Specifies the columns to retrieve (e.g., SELECT name, score to get specific fields).
- **FROM**: Indicates the table to query from (e.g., FROM surveys to pull data from that table).
- Why used: SELECT avoids pulling unnecessary data, improving efficiency; FROM defines the source, allowing focus on one table initially.

**Building On Previous:** With relational knowledge, I could select relevant columns from related tables.

**Why This Unit:** These are the building blocks of every SQL query, enabling data extraction for analysis—like selecting mental health scores from a survey table.

**How I Did It:** Wrote simple queries to retrieve all columns and later specific ones according to project demands, viewing results to understand output.

### 🔄 Key Analysis Steps & Rationale
To meet the project's demand for insightful aggregation on mental health factors, I first sought to understand and familiarize myself with the dataset. I reviewed the table schema and ran exploratory queries (e.g., SELECT * FROM public.students LIMIT 10) to identify what each field represented: stay as duration of residence, todep as a depression index, tosc as social connectedness measure, and toas as acculturative stress level. This step was crucial to select relevant columns—focusing on mental health scores tied to international status—ensuring the analysis addressed how adaptation over time affects well-being.

Once familiar, I crafted the main query to group by stay and compute averages, as the project required summarizing trends rather than raw data. Averages were used because they provide a normalized view of central tendencies across varying group sizes, revealing patterns like increasing stress with longer stays without being skewed by outliers.
Steps Followed:

**SELECT** Clause: Chose stay for grouping, COUNT(*) to count records per stay length (to weigh group sizes), and ROUND(AVG(...),2) for averages of todep, tosc, and toas. Rounding to 2 decimals ensures clean, readable insights—vital for reporting mental health trends.Why? Project demands emphasized aggregation to spot correlations; COUNT adds context on sample reliability.

**FROM** Clause: Specified public.students as the source table.Why? This defines the dataset foundation, building on my initial exploration.
**WHERE** Clause: Filtered to Inter_dom = 'Inter' (international students only).Why? The project focused on international adaptation challenges, excluding domestic data to isolate relevant factors.
**GROUP BY** Clause: Grouped by stay to aggregate metrics per duration.Why? Enables comparison across stay lengths, directly addressing the need to analyze time-based impacts.
**ORDER BY** Clause: Sorted by stay DESC (longest to shortest).Why? Highlights potential progression (e.g., if stress worsens over time), making trends easier to interpret.
**LIMIT** Clause: Restricted to 9 rows.Why? Focuses on top results for concise output, as per project efficiency requirements.

Full Query:
SQLSELECT stay, COUNT(*) AS count_int, ROUND(AVG(todep),2) AS average_phq, ROUND(AVG(tosc),2) AS average_scs, ROUND(AVG(toas),2) AS average_as
FROM public.students
WHERE Inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC
LIMIT 9;

### 📊 Results & Discussion
The query produced a table showing metrics for stay lengths from 10 down to 1:

<img width="1223" height="785" alt="SQL Query and Results" src="https://github.com/user-attachments/assets/6d9b6a34-caa0-48de-aaac-cb730533cf3f" />

(Note: Partial data from image; full results would include all rows.)
Insights from Results:

1. Longer stays (e.g., 10) show smaller sample sizes but varied scores—e.g., higher depression (13) and lower connectedness (32), suggesting isolation over time.
2. Shorter stays (e.g., 1-3) have larger groups with moderate averages, indicating initial adjustment stress that may stabilize.
3. Acculturative stress (average_as) is highest for mid-length stays (e.g., 91 at stay=5), possibly due to cultural adaptation peaks.
Overall, averages reveal a potential trend: depression and stress decrease slightly with shorter stays, but larger samples for short stays imply more data needed for long-term groups.

These findings align with project goals, highlighting where universities might target support (e.g., for students with 4-6 year stays).

### 🏁 Conclusion
This analysis demonstrated how SQL aggregation uncovers mental health patterns, emphasizing the value of averages for trend detection in grouped data. It built my skills in targeted querying for real-world applications.

