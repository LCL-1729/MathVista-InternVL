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
   After execution, two result files will be generated, for example:\n
   • results/internVL2/output_internVL2-1b-mini.json\n
   • results/internVL2/scores_InternVL2-1b-mini.json

