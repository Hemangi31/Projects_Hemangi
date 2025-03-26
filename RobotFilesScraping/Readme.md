# Historical Robots.txt Data Collection and Analysis

## Overview
This project analyzes how online publishers modify their `robots.txt` files over time, specifically focusing on the blocking of AI-based crawlers such as GPTBot, ChatGPT-User, OAI-SearchBot, Google-Extended, PerplexityBot, anthropic-ai, ClaudeBot, and Claude-Web. Using the Wayback Machine, we retrieve and analyze historical snapshots of `robots.txt` files for various publishers.

## Project Structure

- `dataset/`: Contains directories for storing raw and processed data files.
  - robot.ipyb/ : code file 
## Requirements

To run this project, you will need the following Python libraries:
- `requests`
- `pandas`
- `matplotlib`
- `seaborn`
- `waybackpy`
- `numpy`
- `re`
- `datetime`
- `warnings`

Install the required libraries with:
pip install requests pandas matplotlib seaborn waybackpy numpy

# Data Collection Process

Steps:

1. Fetching Historical Snapshots:
The Wayback Machine’s CDX Server API is used to fetch historical snapshots of robots.txt files for each URL within a specific date range (June 2023 - March 2025).

The get_snapshots function retrieves all available snapshots for a publisher.

2. Robots.txt Data Extraction:
Using the fetch_robots_txt_content function, the content of each robots.txt file is retrieved from the Wayback Machine. If successful, the file content is stored along with the timestamp of the snapshot.

3. Handling Errors:
Some retrieval attempts may fail due to network errors or server timeouts. The project implements retry logic to handle temporary failures, retrying up to three times before skipping failed snapshots.

4. Data Cleaning:
Any empty or missing content is replaced with NA. The dataset is then filtered to retain only successfully retrieved snapshots.

5. Crawler Extraction:
A custom function extracts the AI-based crawlers (e.g., GPTBot, ChatGPT-User) from the robots.txt content using regular expressions.

6. Trend Analysis:
The crawlers are exploded into separate rows, and the number of times each crawler is blocked per month is calculated.

7. Comparative Analysis:
A comparative analysis is performed between Group A and Group B publishers, observing trends in crawler blocking over time.

8. Visualizations:
Time-series and bar plots are generated to visualize trends in crawler blocking and the comparative analysis between the two groups.

# Data Processing and Analysis
# Data Flow:
1. Data Collection: Fetch robots.txt snapshots from the Wayback Machine for each publisher.

2. Content Extraction: Extract the content of the robots.txt file for each snapshot.

3. Crawler Identification: Extract AI-based crawlers from the robots.txt content.

4. Trend Analysis: Analyze the trends in blocking AI-based crawlers over time.

5. Comparative Analysis: Compare how Group A and Group B publishers block these crawlers.

6. Visualization: Plot the trends and comparison for insights.

# Key Code Cells:

1. Data Collection: Code for fetching historical robots.txt snapshots and extracting their content.

2. Data Cleaning: Cleaning the dataset and ensuring that only successfully fetched content is included.

3. Crawler Extraction: Extracting AI crawlers from the robots.txt content using regular expressions.

4. Trend Analysis: Processing and visualizing the trends of crawler blocking over time.

5. Comparative Analysis: Creating side-by-side visualizations to compare the trends between Group A and Group B publishers.
Challenges Encountered


Missing Data: Some URLs did not have available snapshots in the Wayback Machine for certain months, leading to gaps in the data for those publishers.
Conclusion

# Future Work

1. Improving retry logic for more robust error handling.
2. Extend the analysis to include additional AI-based crawlers.
3. Explore the use of machine learning to predict when a publisher might block new crawlers based on historical trends.

