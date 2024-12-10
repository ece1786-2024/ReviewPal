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

`data/final_output.txt` contains the outputs of agent 1 and 3 for the 100 reviews.

`data/restaurant_summary.txt` contains the outputs of agent 2 for the 20 restaurants.

`data/final_output.csv` contains the user input and the final output of the system.

## Evaluation

Each review is evaluated based on 4 key criteria:

- Consistency with the user input
- Human language tone
- Effective use of restaurant information
- Overall Quality

Each criterion is rate on a scale of 1 (poor) to 5 (Excellent). Evaluation of each criterion and the summary were under `/data/evaluation`.

## Other Development Files
During the development process, several additional files and scripts were created to experiment with and refine the system. While these are not part of the final pipeline, they represent the intermediate steps or alternative approaches we have explored:

`pipeline/single_agent.py` contains our initial development of a single agent system where the user input is directly transformed to the final output review by prompting GPT-4o.

`pipeline/agent1and2.py` contains our development of a 2-agent system that extracts restaurant information in the provided url and feed that information into an additional agent to produce a key point summary of the retaurant (an example result is shown in `pipeline/RAG_output`). Then, the generation agent takes both the restaurant summary and the user input to generate the review. 
