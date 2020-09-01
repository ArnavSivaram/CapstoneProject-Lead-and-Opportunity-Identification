# CapstoneProject-Lead-and-Opportunity-Identification
This is a comprehensive data science project that I worked on (from Feb to May '20) with a Fortune 500 Chemicals manufacturing company where I had to build text classification models and a Power BI dashboard to help them identify leads and opportunities for their business.

### Situation
I recently spearheaded a data science project as analytical lead for a Fortune 500 chemical manufacturing company, mainly involved in providing hygiene and sanitation solutions to various industries. The client had a very large repository of 15 million failed inspection comments (known as ‘violation comments’ as a failed inspection is treated as a violation of a specific health authority guideline) written by health department inspectors as a result of audits of food establishments and chains that it wanted to leverage to identify leads and opportunities for their businesses. Until this project, the client was not able to fully exploit it due to each comment being categorized into one of four very broad categories, which provided little insight into the specific pain-points of customers.

### Task
Thus, the project involved – <br/>
* Classifying 15 million textual comments into granular, actionable categories <br/>
* Exploring data trends to identify leads and opportunities using the 15 million classifications <br/>
It also involved provision of ready tools for the client to undertake classification and data exploration in future by themselves.

### Action
**Text Classification** <br/>
*Initial text classification models* <br/>

The client’s marketing team had manually annotated about 2 million inspection comments of their actual customers themselves, while they were serving those clients, over the years. This categorization was done according to a classification provided by the FDA, which contained 54 categories that a possible violation (failed inspection) could belong to. I used this data to train and test my models in Python, before deploying it on the 15 million ‘unlabeled’ dataset. To train the model, I first used standard natural language preprocessing (NLP) steps like tokenization and stemming to generate the corpus vocabulary. After splitting the 2 million row dataset into train and holdout test dataset components, I transformed the train dataset into a TF-IDF matrix. I used this to dataset to train several models using different algorithms and tuned the models’ hyperparameters using cross-validation. Then, I transformed the held-out test dataset into a TF-IDF matrix and evaluated out-of-sample performance of the different models on this dataset. <br/>
Finally, I selected the best performing model, which was a gradient-boosted tree (using Microsoft’s LightGBM). I used this gradient-boosted tree to predict categories of the 15 million unlabeled data.

*COVID-specific classification models* <br/>

Midway through the project, the COVID pandemic struck and began disrupting the client’s businesses. The focus of the project changed, and the client wanted to dive further into 10 of the 54 FDA categories that would be more closely related to COVID-transmission risk. For each of these 10 categories, the client wanted to predict subcategories of issues. To tackle this task, I had to build 10 additional models for each of those questions. The challenge here was that I had substantially lesser data for training these models. To make sure I achieved good predictive performance, I used a combination of 3 different algorithms in a stacked generalization framework. I further improved performance for 3 specific FDA categories by implementing an Error Correcting Output Coding (ECOC) method from scratch over the stacked models. <br/>

Finally, I used these models to predict the subcategories of problems that were being faced in the market, for the 10 specific FDA categories that could be closely linked to COVID-transmission risk.

**Metrics Development** <br/>
Once I had my classifications ready from the initial text classification models as well as COVID-specific text classification models, I needed to develop metrics to quantify the opportunity/leads in the market. I worked cross-functionally with the R&D, Marketing, Analytics, and Sales teams to develop metrics such as inspection failure rate, violation rate, re-inspection failure rate, re-inspection violation rate, COVID-related category failure rate, COVID-related category violation rate, etc.

**Power BI dashboard** <br/>
After developing metrics, I joined all the 15 million rows of the data that my models had classified with other tables (data about facilities, states, violation categories, etc.), that I had access to and I created a Power BI dashboards for the client. I had all the metrics listed at the top, and different views customized to the different audiences within the client organization that would have access to the dashboard. For the sales executives, territory managers, and General Manager, there were charts on the state-wise distribution of violations, top accounts in terms of the metrics, top FDA violations categories, and number of violations over time. For the food safety head (R&D) and her team, I had included charts on the state-wise distribution of violations, line charts by Center for Disease Control (CDC) category, violations by type of restaurant, and top FDA-level violation categories. Finally, I also had a view that was specific to COVID-related FDA category charts. <br/>

**Association Rules Mining** <br/>
In addition to creating the dashboard and sharing insights on top violation categories, I also mined the dataset for association rules, segmented by business entity type. This gave insight into which categories of violations tended to co-occur and how that differed between different types of restaurants. This helped our client identify cross-selling opportunities in the market.

### Results
The classification models that I built brought value to our client in 4 ways - coverage and scalability, speed in the market, granularity in understanding, and relevance to the immediate business situation that was COVID. The dashboard that I designed enabled took this a step further and enabled organization-wide adoption by technical and non-technical audiences. The client took the solutions provided live at the end of May and used push notifications of my models’ classifications to their sales executives. I presented to a forum consisting of the Chief Digital Officer, General Manager, Enterprise Analytics Director, Marketing Director and Director of Analytics (for some of the Lines of Business), and my work received very positive feedback. Finally, my team won the ‘Adaptability’ award for quickly pivoting focus to COVID-related opportunity analysis and achieved a 200/200 client score.

