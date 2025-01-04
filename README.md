1. Environment Setup
   The requirement.txt file contains the versions of the relevant packages. It’s best to use the package versions specified in this file.
2. Data Preparation
   Create a folder named images inside the "data" directory. Extract the images from the downloaded compressed file from Hugging Face and place them in this folder.
   Dataset link:
   (Only the images.zip file needs to be downloaded.)
3. Model Preparation
   Download the required model into the models/model/InternVL2-1B folder.
   Before downloading a new model, ensure the contents of the InternVL2-1B folder are cleared.
4. Model Files
   The model file is located at models/InternVL2.py.
5. Execution:
   a. python generate_response.py --model internVL2 --output_dir ../results/internVL2 --output_file output_internVL2-1b-mini.json
   b. python extract_answer.py --output_dir ../results/internVL2 --output_file output_internVL2-1b-mini.json
   c. python calculate_score.py --output_dir ../results/internVL2 --output_file output_internVL2-1b-mini.json --score_file scores_internVL2-1b-mini.json
6. Result Files
   After execution, two result files will be generated, for example:
   • results/internVL2/output_internVL2-1b-mini.json
   • results/internVL2/scores_InternVL2-1b-mini.json
7. Issues
   The OpenAI API call often fails... When the API call fails, the original code will attempt to retry. Pay attention to this during execution.

Openai Key in .env:
OPENAI_API_KEY=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

Fixing:
utilities.py (line 188):
if n == 1: # prediction = response['choices'][0]['message']['content'].strip()
prediction = response.choices[0].message.content.strip()

problem with calculate_score.py (line 152):
choices = problem['choices']
question_type = problem['question_type']
answer_type = problem['answer_type']
precision = problem['precision']
extraction = problem['extraction']

        if 'answer' in problem:
            answer = problem['answer']
        else:
            # using a lot of try except states
            try:
                answer = gts[pid]['answer']
                problem['answer'] = answer
            except KeyError:
                continue
        # normalize the extracted answer to match the answer type
        prediction = normalize_extracted_answer(extraction, choices, question_type, answer_type, precision)
