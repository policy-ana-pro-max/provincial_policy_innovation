# provincial_policy_innovation

The "data-pre_processed" folder contains government work reports from 31 provinces and the State Council for the years 1998-2023. These reports have been manually screened to remove irrelevant phrases for policy innovation calculations, such as "make the sky bluer here." The beginning of the following year's work plan is marked with "二&、". Please note that some provinces have missing reports for the 1998-2002 period. Additionally, policy innovation calculations require sacrificing some early data to address the cold start problem. Therefore, we use data from 1998-2023 to derive valid policy innovation data for 2003-2023.

Data Processing Workflow:
First, using code-text preprocess.ipynb, each report is broken down into short sentences. For each short sentence, its keyword set is tagged based on syntactic dependency relations.

Next, innovation_adoption_judge.ipynb calculates the number of innovations adopted in each report. This step utilizes pre-trained word vectors. Due to their large size, the specific pre-trained vectors I used are not uploaded. You can download them from https://github.com/Embedding/Chinese-Word-Vectors or use other more effective pre-trained vectors.

Finally, generation&borrowing_judge.ipynb further determines whether each innovation adopted by a province is generated or borrowed. Due to limited computational resources, I've set up the process to run year by year. I also aggregate previous innovation generations and prioritize previously borrowed innovations in the search queue. Furthermore, innovation generations that haven't been borrowed for over 10 years are removed from the search queue. These measures are implemented to accelerate the training process.
