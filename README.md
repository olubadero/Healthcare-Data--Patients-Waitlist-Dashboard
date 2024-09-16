# Healthcare-Data Patients-Waitlist-Dashboard

**DATASET**: 

This is a publicly available healthcare data about patient waiting list. It contains 2 types of data i.e. Inpatient (a patient that stays in a hospital whilst under treatment) and Outpatient (a patient who receives treatment without being admitted in the hospital) from 2018 - 2021. Each year and patient type for all 4 years had over 55,000 rows and 7 columns each, so a total of 453119 rows and 8 columns were analysed after all datasets were merged and cleaned.

**Inpatient 2018 Dataset Preview**
![Screenshot (26)](https://github.com/user-attachments/assets/cfafd5ac-cc09-4279-8c58-bb6c29601f37)

**Outpatient 2018 Dataset Preview**
![Screenshot (28)](https://github.com/user-attachments/assets/1d299689-a550-4c9e-9c55-8936aca957c7)


**Objective of the Project**:
1.	Track current status of patient waiting list
2.	Analyze historical monthly trend of waiting list in inpatient & outpatient categories
3.	Detailed specialty level & age profile analysis

**Key Metrics Required**:
1. Average & Median waitlist
2.	Current Total Waitlist in comparison with the previous year Waitlist

**Views Required in Dashboard**: 
1. A Summary page
2.	A Detailed page for granular analysis.


**Data Transformation & Modelling Phase**: This was done in Power Query and Model View 
- Used the folder connector to import the data from 2018 - 2021 into Power Query
-	Checked & changed data types 
-	Checked total row count
-	Removed blank row
-	Trimmed data to ensure consistency
-	Changed column header names to ensure uniformity between all outpatient and inpatient data
-	Inserted Case_Type column in the Outpatient folder to enable merging of both files. This column will help to differentiate both case types when the entire folder is merged.
-	Appended both inpatient and outpatient table into one dataset creating over 450,000 row data
-	Renamed the appended table and loaded the transformed table.

![Screenshot (32)](https://github.com/user-attachments/assets/402a5aa9-593f-4901-967c-d90dc1f0b937)

-	A specialty mapping table was also created and imported. This provides what part of the body each specialty field was responsible for treating. Relationship was created between the specialty mapping and combined data table in the data view.

![Screenshot (31)](https://github.com/user-attachments/assets/83d4fecd-fd5a-4f95-bc64-51710cd16ef9)

**DAX Functions used for Visualization**: 

**Calculate the current waitlist of the most current date**: 
- CALCULATE(SUM(All_Data[Total]), All_Data[Archive_Date] = MAX(All_Data[Archive_Date]).

**Calculate the current waitlist of exactly a year before the most current date**: 
- CALCULATE(SUM(All_Data[Total]), All_Data[Archive_Date] = EDATE(MAX(All_Data[Archive_Date]), -12))

**Median Waitlist**: 
- MEDIAN(All_Data[Total]) 

**Average Waitlist**: 
- Average(All_Data[Total])

**Creating a dynamic chart title that changes when a certain value is selected in the dashboard**:
-	SWITCH(VALUES('Calculation Method'[Calc Method]), "AVERAGE", "Key Indicators - Patient Wait List (Average)", "Median",  "Key Indicators - Patient Wait List (Median)")

View [insights]()


