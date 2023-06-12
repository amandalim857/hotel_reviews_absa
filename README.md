# Aspect-Based Sentiment Analysis on Hotel Reviews

## The Problem:
Hotel booking websites like TripAdvisor and Booking.com are a vast and valuable, yet untapped resource of feedback that hotels can use to improve their ratings and attract more customers. However, hotel staff do not have time to trawl through hundreds of written reviews to gather all the areas of improvement, and even numerical ratings are insufficient, as they cannot tell the hotel _how_ to improve. If there is a poor service rating, is it due to the front-counter experience, the room service or the cleaning service?

## How this project solves it
Aspect-Based Sentiment Analysis (ABSA) identifies aspects and their corresponding perception (positive, neutral, negative) within a sentence. For example, the review "the concierge staff were slow and rude to me" would yield the aspect "concierge" with sentiment "negative". This is a perfect method to use on unstructured hotel review data. By using an averaged scoring system on the most common aspects that appear in the reviews, not only can hotel staff zoom in on the exact issue bringing their ratings down, but also know more about the common aspects that their guests take note of in their feedback, both positive and negative. From the previous example, if "concierge" has the most complains, the staff now know their poor service rating is due to the counter staff, and focus on retraining those staff. The most benefits are achieved without wasting time on reading through every single feedback just to find the area of dissatisfaction.

## Pipeline
### Resources
- The model used for training and testing was from the [PyABSA](https://github.com/yangheng95/PyABSA) repository. Due to time constraints and limited labelled data, the model, which had been trained on restaurant reviews, was further trained on 400 hotel reviews via transfer learning. 
- The labelled hotel review data was taken from **fill in**. 
- Data from Britannia Hotel was withheld and used for inference, pretending that this hotel was our client who wanted to identify their top areas of improvement.
- blah, blah and blah are created during the pipeline process.

1. Reformatted hotel reviews data into the accepted labelled format that the model took in for training data.
2. Reformatted model output to identify the frequencies of each aspect. The top 50 were chosen and manually sorted into regular hotel feedback categories.

| Food          |   Service     |     Cost      |  Room Quality |  Amenities    |   Location    |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| food          | staff         |   price       |  bathroom     |     wifi
| bar           | service       |   rates


3. Infer the results of Britannia reviews from the model, the aspects were sorted into the predefined categories in the table and each category assigned a rating based on the formula: $$\frac{[(positive freq) + negative freq(-1)]} {aspect freq}$$

## Usage of .ipynb file
- Access the ipynb file, and load the files from `/resources`. 
- The files in `/resources` are all the initial data used in the project; `/resources/output` are the files generated throughout the pipeline process as output for other functions or as final output (for example, the model checkpoints after transfer learning, or the inference json results etc) 

## Limitations and future improvements
-  The main constraints are due to the limited labelled data available. Data Augmentation can be used in future expansions to generate larger amounts of data for training.