# Tinybird "St. Albnas" Hackathon
*Clean some data, win some swag*

<details>
<summary><h2>The Problem</h2></summary>

The "St. Albnas" problem has become quite a meme on the internet. It seems to have originated [here](https://www.linkedin.com/posts/aesroka_management-we-have-great-datasets-the-datasets-activity-7072180991229874176-p8PX/) (h/t to Adam Sroka).

![image](/img/st-albnas.webp)

The meme captures a well known issue with data quality: Free-text fields aren't consistent!

## The Goal
Write some code (SQL, GPT, regex, whatever you want) that will accurately, precisely, and consistently converge all of the elements in the [`positives.txt`](/positives.txt) file to the correct spelling: `St. Albans`.

The code should repeatably converge as many of the entries as possible into the correct spelling while also avoiding false positives (e.g. you can't just replace the entire string with `St. Albans` everytime by brute force). To ensure that your code avoids false positives, we've included a [`negatives.txt`](/negatives.txt) file. Your code should avoid converting any of these to `St. Albans`.

## The Rules
- To submit an entry, clone this repo, checkout a new branch, and submit a pull request.
- Use whatever language you want, whatever libraries you want, whatever. But it must be code and it must compile. (You can use GPT or any other LLM, but simple text GPT prompts will not be accepted!)
- Any entry that converts the elements by brute force (i.e. by individual string matching) will be rejected.
- Valid entries must include:
  - All necessary code to do the data cleansing
  - A README explaining how to run the code over the included `.txt` files.
  - A demonstration of the results you achieved (image, file, etc.) that should be repeatable
  - Optional: Include your Twitter handle in your GitHub profile if you'd like to be mentioned on Twitter.
- Submissions are due by Friday, July 21st at 5 PM GMT
- Tinybird employees may not participate

## Scoring
Aim for [Accuracy (ACC)](https://en.wikipedia.org/wiki/Accuracy_and_precision#In_binary_classification), measured as (true positives + true negatives) / (all possibilities).

For example, a submission that accurately converts 15 out of the 17 elements in `positives.txt` and accurately ignores 24 out of the 25 elements in `negatives.txt` would score (15 + 24) / (17 + 25) = 92.8%

Submissions that correctly convert all 17 of the elements in `positives.txt` and none of the 25 elements in `negatives.txt` to `St. Albans` would score a 100%.

## Participation Award!
Let's be honest, this problem isn't *that* hard, but it should be fun! All you need to do is submit a working attempt, and you'll get $20 off at [The Tinyshop](https://shop.tinybird.co). That's enough for a t-shirt, a coffee mug, or 2 sticker sheets!

Also, as an incentive to score well, we'll tweet the final leaderboard when this ends :).

#### Here's what you have to do to get the participation award:
- Submit a valid entry (see above) 
- Star this repo
- Follow Tinybird on Twitter [@tinybirdco](https://twitter.com/tinybirdco) and/or LinkedIn
- Share your submission on Twitter/LinkedIn using #stalbnashackathon (tag us too!)

## Need help?
Join our [Community Slack](https://www.tinybird.co/join-our-slack-community)!
</details>

## The Solution

A Python script designed to analyze the similarity between words and a target word using the Jaro-Winkler similarity metric. The purpose of this script is to categorize words as either "converted" (similar to the target word) or "ignored" (dissimilar to the target word) based on a predefined similarity threshold. The script reads input data from two txt files, "positives.txt" and "negatives.txt," containing lists of words to be analyzed.

### Prerequisites

1. Python 3: The script requires Python 3 to be installed on your system.

2. Dependencies: Make sure to install the required dependencies using the following command:

```bash
pip install -r requirements.txt
```

### Usage

1. Prepare the Data Files:
   - Create two txt files: "positives.txt" and "negatives.txt."
   - Each file should contain a list of words (strings) to be compared against a target word.

2. Run the Script:
   - Open a terminal or command prompt and navigate to the directory containing the script and data files.
   - Execute the script by running the following command:

```bash
python solution.py
```

### Script Functionality

1. `load_data(file_name)`: This function reads a txt file containing a list of words and returns the list as a Python object.

2. `calculate_accuracy()`: This function calculates the accuracy of the word similarity analysis. It computes the ratio of converted positive words and ignored negative words to the total number of positive and negative words. The accuracy is expressed as a percentage and rounded to two decimal places.

3. `display_metrics(metric, metric_name, sort_ascending=True)`: This function displays the analysis results for a given metric in a tabular format using the Pandas library.

4. Main Execution:
   - The script defines a target word, "St. Albans," and a similarity threshold of 0.85.
   - The script reads the positive and negative word lists from "positives.txt" and "negatives.txt," respectively.
   - For each word in the positive list, the script calculates its similarity score using Jaro-Winkler similarity with the target word. If the score is equal to or greater than the threshold, the word is considered a "converted positive"; otherwise, it is an "ignored positive."
   - For each word in the negative list, the script calculates its similarity score. If the score is less than the threshold, the word is an "ignored negative"; otherwise, it is a "converted negative."
   - Finally, the script displays the results in tabular format, showing the "converted positives," "ignored positives," "converted negatives," and "ignored negatives." Additionally, it shows the overall accuracy of the word similarity analysis.

### Output

![image](/img/output_1.png)
![image](/img/output_2.png)
![image](/img/output_3.png)

<details>
  <summary>Swag 🧢</summary>
  
  <img src="swag.png" alt="Image Alt Text" width="50%">
</details>

