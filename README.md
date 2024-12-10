# ReviewPal

## Summary

ReviewPal is a restaurant review generation system that leverages LLMs to help users turn their quick thoughts into high quality restaurant reviews.

## Data

Data consists of 100 authentic, high-quality reviews that

- 50% from Google; 50% from Yelp
- 20 different restaurants
- 72 positive reviews and 28 negative reviews

Raw data is further processed by `generate.py`, which reverse-engineered the collected reviews to brief ideas that simulate user inputs.

The processed dataset is stored in `labeled_output.csv`.

## Pipeline

### Run the pipeline

`pipeline/pipeline.py` contains the final architecture of the system.

To run the system, first set the OPENAI_API_KEY environment variable

```linux
export OPENAI_API_KEY="PUT_YOUR_KEY_HERE"
```

Run `pipeline.py` and save the output of the three agents for the 100 reviews.

### Outputs

`final_output.txt` contains the outputs of agent 1 and 3 for the 100 reviews.

`restaurant_summary.txt` contains the outputs of agent 2 for the 20 restaurants.

`final_output.csv` contains the user input and the final output of the system.

## Evaluation

Each review is evaluated based on 4 key criteria:

- Consistency with the user input
- Human language tone
- Effective use of restaurant information
- Overall Quality

Each criterion is rate on a scale of 1 (poor) to 5 (Excellent). Evaluation of each criterion and the summary were under `/data/evaluation`.
