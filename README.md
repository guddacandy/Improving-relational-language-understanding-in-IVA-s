# Improving-relational-language-understanding-in-IVA-s

Table of Contents

PROJECT: IMPROVING RELATIONAL LANGUAGE UNDERSTANDING IN INTELLIGENT VIRTUAL AGENTS (IVAS)	2

1.0 OVERVIEW	2

1.1	Introduction	2

1.2	Challenges	2

1.3	Proposed Solutions	2

1.4	Brief Conclusion	3

2.0 BUSINESS UNDERSTANDING	3

2.1 Problem statement	3

2.2 Audiences / Stakeholders	3

2.3 Objectives	3

3. 0 DATA UNDERSTANDING AND PREPARATION	4
   
3.1 Data Understanding	4
   
3.1.1 Source of Data	4

3.1.2 Dataset Details/ Descriptions	4

3.2 Data Analysis	6

3.2.1 Univariate Analysis	6

3.2.2 Bivariate Analysis	7

4.0 MODELING	7

4.1 Evaluation	7

5.0 CONCLUSION AND RECOMMENDATION	8

5.1 Next Steps	8






PROJECT: IMPROVING RELATIONAL LANGUAGE UNDERSTANDING IN INTELLIGENT VIRTUAL AGENTS (IVAS)

1.0 OVERVIEW

In order to promote more efficient and natural human-agent interactions, this project aims to improve Intelligent Virtual Agents' (IVAs') relational language understanding skills. The goal of this project is to enhance the overall user experience and empower intelligent assistants (IVAs) to execute tasks more accurately and efficiently by enhancing their capacity to understand complex relationships expressed in language.

1.1	Introduction

Intelligent virtual agents, or IVAs, have become essential parts of many applications, from virtual assistants to chatbots for customer service. However, IVAs' efficacy is frequently constrained by their capacity to accurately comprehend and react to human language, especially when it comes to intricate relational concepts. By concentrating on enhancing IVAs' relational language understanding, the project aims to overcome this difficulty and close the gap between machine comprehension and human communication.

1.2	Challenges

Several challenges hinder IVAs' ability to understand relational language effectively:
1.	Semantic Complexity: Relational language frequently contains intricate semantic structures and nuanced expressions that are difficult for conventional NLP models to understand.
2.	Context Sensitivity: In order to fully comprehend relational language, one must take into account the conversation's larger context, which includes prior exchanges and contextual elements.
3.	Real-Time Responsiveness: In order to preserve a natural conversation flow, IVAs must process language inputs quickly, which places limitations on their efficiency and computational resources.
   
1.3	Proposed Solutions 

This project proposes a comprehensive approach to address the challenges in relational language understanding:
1.	Advanced Natural Language Processing (NLP) Models: Develop and improve neural network structures designed expressly to precisely capture and represent the semantics of relational languages.
2.	Contextual adaptation: Enhance contextual sensitivity by implementing mechanisms that allow intelligent virtual assistants (IVAs) to modify their comprehension of relational language in response to contextual cues and user intent.
3.	Optimize model architectures and algorithms to ensure real-time responsiveness and efficient utilization of computational resources.
1.4	Brief Conclusion
In conclusion, the project on improving relational language understanding in IVAs represents a critical step towards advancing the capabilities of virtual agents to interact more intelligently and effectively with users. By addressing the challenges associated with relational language comprehension and proposing innovative solutions, the project aims to elevate the state-of-the-art in IVAs and unlock new opportunities for their integration across various domains and applications.

2.0 BUSINESS UNDERSTANDING

2.1 Problem statement

When interacting with customers, existing Intelligent Virtual Agents (IVAs) often find it difficult to decipher and react correctly to relational language cues. This shortcoming impairs customer satisfaction and experiences, as well as the IVAs' ability to build rapport, effectively handle customer needs, and cultivate positive relationships. Thus, there is a pressing need for processes and instruments that enable IVAs to recognise and react to relational language cues with precision, improving the calibre of customer service encounters and increasing customer satisfaction levels.

2.2 Audiences / Stakeholders

Our audiences and key stakeholders include:
1.	Kenya Airways
2.	JamboJet
3.	Safaricom
   
2.3 Objectives

Our objectives include:
1.	Develop algorithms and models to enable IVAs to comprehend relational language expressions comprehensively, including complex relationships and subtle nuances. (MAIN)
2.	Enhance IVAs' ability to understand relational language in various contexts, adapting their interpretations based on the specific scenario and user intent.
3.	Optimize the computational efficiency of the relational language understanding models to ensure real-time responsiveness of IVAs during interactions.
   
3. 0 DATA UNDERSTANDING AND PREPARATION
   
3.1 Data Understanding
3.1.1 Source of Data
The RSiCS dataset was collected from commercial customer service IVAs and the TripAdvisor airline forum (https://nextit-public.s3-us-west-2.amazonaws.com/rsics.html)).
3.1.2 Dataset Details/ Descriptions
The dataset contains 4 files and they include 
1.	x_y_align.csv
Captures alignment and agreement metrics between Annotator A (x) and Annotator B in a group for specific requests.
Columns:
•	Annotator A ID: x
•	Annotator B ID: Annotator that the alignment score with x is calculated against.
•	Group ID: The group of 4 annotators that the compared users belong to.
•	Dataset ID: Dataset y that the request originated from.
•	Request ID: Unique ID of a request to allow joining between different files.
•	Text: The original request text.
•	Annotator A Text: The request text with selections from annotator A contained within [ and].
•	Annotator B Text: The request text with selections from annotator B contained within [ and].
•	Length: The character length (n) of the original request text in column 6.
•	Error: The number of character positions (e) where the binary determination of A and B do not agree.
•	Alignment Score: The alignment as calculated by align = (n - e) / n.
•	Agreement: Whether or not A and B agree that any selection is necessary.

2.	all_data_by_threshold.csv
Merges selections and determines user intentions.
Columns:
•	Dataset ID: Dataset that the request originated from.
•	Group ID: The group of 4 annotators that the selections originated from.
•	Request ID: Unique ID of a request to allow joining between different files.
•	MultiIntent: 1 if at least one annotator flagged the text as containing more that one user intention, 0 otherwise.
•	Threshold: The threshold (i) to merge selections by.
•	MergedSelections: If at least i annotators marked a character as unnecessary then it will be contained within the selected portion denoted by [ and ].
•	Unselected: All text from MergedSelections not contained by [ and ].
•	Selected: All text from MergedSelections contained by [ and ].
•	Removed: Amount of text removed from the original request by the merged selections: length(Selected) / n.
3.	tagged_selections_by_sentence.csv
Identifies relational language in user requests.
Columns:
•	Dataset ID: Dataset that the request originated from.
•	Group ID: The group of 4 annotators that the selections originated from.
•	Request ID: Unique ID of a request to allow joining between different files.
•	Threshold: The threshold (i) to merge selections by.
•	MergedSelections: If at least i annotators marked a character as unnecessary then it will be contained within the selected portion denoted by [ and ].
•	Unselected: All text from MergedSelections not contained by [ and ].
•	Selected: All text from MergedSelections contained by [ and ].
•	Greeting: If a greeting of some kind (Hi, How are you) is present in Selected
•	Backstory: If self-exposure language is present in Selected. The user is telling the audience about themselves, their situation, what led them to contact the agent or ask their question.
•	Justification: If justification language is present in Selected. The user is giving facts to build credibility that their request or statement is true. Also can be why they need resolution or a consequence if something is not resolved.
•	Rant: If ranting is present in Selected. Excessive complaining or negative narrative.
•	Gratitude: If some expression of gratitude to the audience for past or future help is present in Selected.
•	Other: If some or all of the highlighted section does not contain any relational language in Selected. Could be additional facts the user gave but annotators determined was unnecessary to determine their intention, or a general question such as Can you help?.
•	Express Emotion: If any emotional language not covered by Rant is present in Selected.
4.	all_multi_intent.csv
Flags requests with multiple intentions for intent detection strategies.
Columns:
•	Dataset ID: Dataset that the request originated from.
•	Group ID: The group of 4 annotators that the selections originated from.
•	Request ID: Unique ID of a request to allow joining between different files.
•	Text: The original request text.
•	Annotator x: Will be 1 if annotator x believed more than one intent was present in the text, 0 otherwise.
3.2 Data Analysis 
The following steps were followed in preparing the data; 
	 Importing the necessary libraries. 
	 Loading the dataset from the CSV format it was stored in.
	Cleaning datasets.
	Creating a new data frame with the necessary columns for our research.
	Exploratory Data Analysis (EDA).
3.2.1 Univariate Analysis
A word cloud visualization to represent the frequency of words in the text data, providing a quick and visually appealing way to understand the most common words in the text.
 
3.2.2 Bivariate Analysis
A heatmap to visualize the correlation between pairs of numerical variables (Alignment Score, Length, and Error). 
 
a.	Alignment Score vs. Length: Negative correlation of -0.293, indicating a slight decrease in alignment score as text length increases.
b.	Alignment Score vs. Error: Strong negative correlation of -0.856, showing that higher errors correspond to lower alignment scores.
c.	Length vs. Error: Moderate positive correlation of 0.619, suggesting longer texts tend to have higher error rates.
4.0 MODELING
4.1 Evaluation





5.0 CONCLUSION AND RECOMMENDATION
5.1 Next Steps


