
# Exploratory Data Analysis Exercise

### Objective: 

> Understand the business and extract key information from customer briefings  

**Technical Steps:** 
- Combine multiple data sources where necessary
- Perform Exploratory Data Analysis   

**Mathematical Steps:** 
- Calculate descriptive statistics  

**Data:** 
- Located in the `data.zip` file in this repository

## Context 
A Muesli distribution company has approached you to help them understand their delivery process. They want to develop KPIs to help them keep track of the health of their business in order to improve the service they offer their customers.

<font color="yellow">The warehouse manager</font> described the workflow as follows:
<ol>  


Order received (Day 1) → Order processed in warehouse and made ready to ship (normally 2 days) → Order leaves warehouse in truck on the following day → Order delivered to customer 

Transportation is handled by a third-party logistics company.

The Muesli company has provided a list of their transactions over the past few years. They claim to have complete data on the **Order Date** and the On **Truck Scan Date**, but have limited visibility of what happens in between or after. <font color="pink">Occasionally</font>, they have sent <font color="pink">interns</font> into the warehouse to record the **Ready to Ship Date** for as many orders as possible. According to the warehouse manager, they have not significantly changed their processes in the past year, so they believe this data should be a good estimate.

Customers can send orders every day, but the warehouse only operates from Monday to Friday. Therefore, any orders received on weekends are processed on Monday.

Trucks leave the warehouse on Mondays, Wednesdays, and Fridays. Orders are shipped the day after they are ready for shipping (or two days later if there is no truck). Customers can pay for Express Processing, which ensures that orders leave on the truck the same day they are ready for shipping.
</ol>

<font color="yellow">The logistics company</font> reports:
<ol>  
They have an average delivery time of 3 days to all locations. They transport goods on weekends but only deliver to customers from their local distribution centers on weekdays. The Muesli company has provided <font color="pink">some data</font> on exact delivery dates for a number of shipments, gathered via <font color="pink">marketing promotions</font> where customers scanned a QR code on the package to register for a prize. (We assume customers always scanned the code on the day of arrival → <b>Arrival Scan Date</b> ).
</ol>

## Deliverable:
A 10-15 minute presentation to the class or stakeholders describing the business's performance based on the developed metrics. Include why these specific metrics are important, what they reveal about the business as described by the employees, and how you technically developed these metrics from the given data. (more detail in: [Visualise and Communicate](#visualise-and-communicate) below)

## Workflow:   
### Understand Business Problem and Potential Solution
1. Map out the order process in a flowchart using tools of your choice.
2. Invent metrics that would be useful for tracking performance overall and at each stage.
3. Label the flowchart with any logic that affects how orders move through the stages. 
4. Include notes about assumptions the company and suppliers make regarding processing time for each stage.

### Descriptive Analytics

- Load the provided data into pandas and perform simple Exploratory Data Analysis (EDA) to describe the data, including descriptive statistics, identification of missing values, and any outliers.  
  
- Take the assumptions from the warehouse manager (as you understood them) and compare them to your findings in the data.

- Prepare your data by combining (where needed) and augmenting it in any way to generate the data needed to validate the assumptions.

- Match/Mismatch? Analyze each step of the ordering process separately and quantify the extent of mismatches (in percentages).
</ol>

### Diagnostic Analytics

- Can you help to understand what leads to the increased time in the delivery process?

  - Perform further exploratory data analysis to understand the **time taken** in each step of the order process and the **range of values** for each metric.
  - Identify problematic data or outliers.
  - Show the **average processing time** for orders and how much **variation** exists for each stage.

- Evaluate whether the data align with the explanations of the processes given by the company.

- Identify any steps that have 'concerning' levels of reliability.

### Visualise and Communicate

- Use a Jupyter notebook to organize the text, code, and visualizations that can be delivered to the customer.

- Present your output as slides. 
  - Please create your slides in your Google Drive [Muesli EDA Project Folder](https://drive.google.com/drive/folders/1Q6ZD62JsfhvMze5YTT2B9ZYVePwD_j9p). 
  - Discuss why you have done things, what your intentions were, and how you technically developed the analysis, including screenshots of notebook code and output as necessary. 
  - The expectation is a 10-15 minutes presentation to the class. 
  - Think of it as a stakeholder presentation with technical elements.
  
### EXTRA CREDIT  
- The company would like to know how long it takes for an order to be delivered to the customer, depending on the day it is received. They would like to know both the average delivery time and the 95th percentile of delivery times (i.e., the number of days within which 95% of orders are delivered).
  
  > Consider building a new dataset made up of **simulated data** that is randomly selected from the partial datasets available. This will create a set of simulated orders that can be measured to show the distribution of delivery times.  
  >
  >You can randomly sample from a column of data while ignoring missing values, allowing you to fill in those missing values using the distribution of non-missing data. The code for this is below:
  >
  >```python
  >df_new["processing_time"] = df["processing_time"].apply(
  >  lambda x: np.random.choice(df["processing_time"].dropna().values) if np.isnan(x) else x)
  >```

- The company would like to reduce lead time but doesn’t know the best approach. 
  - The logistics provider has stated that they can offer daily pickup (Monday to Friday) for an additional cost. 
  - Alternatively, the warehouse could hire more people to handle all shipments as ‘Express’. 
  
  Assuming the costs are equivalent, use simulation models to determine which option would lead to better improvement in the 95% delivery promise.







