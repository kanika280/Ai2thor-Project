#AI2THOR Object Search Agent

Overview
This project demonstrates a socially intelligent agent capable of collaborating with a human to locate and identify objects in simulated AI2-THOR environments. The agent minimizes physical actions by prioritizing dialogue-driven interactions and provides visual and verbal feedback for efficient and accurate object identification.

Features
Human-Agent Interaction: Uses natural language understanding (NLP) to interpret user descriptions.
Dialogue-Driven Search: Engages in iterative dialogue to clarify ambiguous descriptions and confirm object identification.
Efficient Navigation: Minimizes physical movements by leveraging user input and scene context.
Multimodal Feedback: Combines verbal and visual communication for enhanced understanding and alignment.
Structured Documentation: Logs interactions and actions in structured JSON files for evaluation.

Requirements
Python 3.8+
AI2-THOR
spaCy
Transformers
OpenCV
NumPy
Other dependencies listed in requirements.txt

Install the required dependencies using:
pip install -r requirements.txt

How to Run
Start the Controller:
The script initializes an AI2-THOR controller with default settings.
Describe the Object:
Input a description of the object you're searching for (e.g., "red cup on the table").
Interact with the Agent:
The agent uses dialogue to clarify ambiguous descriptions or confirm identified objects.
Receive Feedback:
The agent displays images of detected objects for validation and logs all interactions.
Exit:
Type "exit" or "quit" to terminate the program.

Run the program using:

python <ai2thorprojectdefault>.py

Project Structure

├── images/                  # Directory for saving images of detected objects
├── object_details/          # Directory for saving object details
├── emissor/                 # Directory for interaction logs and metrics
├── <script_name>.py         # Main script
├── README.md                # This README file
├── requirements.txt         # Required Python packages

Key Functions
1. Main Functions
main_loop(): Core function for initiating the interaction and managing the agent's operations.
explore_room(leolaniClient): Explores the room to detect visible objects.
confirm_candidates(candidates, description, visible_objects, leolaniClient): Confirms object candidates based on user input and visible objects.
2. Helper Functions
safe_reset_scene(scene_name): Safely resets a scene in AI2-THOR.
parse_description(description, visible_objects): Parses user-provided descriptions using spaCy.
filter_candidates_by_context(candidates, spatial_context, reference_objects, attributes, leolaniClient): Filters objects based on spatial relationships and attributes.
generate_clarifying_question(description): Generates clarifying questions using GPT-2.
orient_and_display_object(obj, leolaniClient): Orients the agent towards an object and displays it.
3. Utility Functions
display_image(frame, object_type): Saves and displays an image of a detected object.
save_object_details(obj): Saves details of a confirmed object.
Code Design
Modularity: Each function serves a distinct purpose, ensuring reusability and clarity.
Naming Convention: Follows descriptive and consistent naming practices.
Documentation: Functions are commented for clarity, and external modules/models are referenced explicitly.
Logging: Metrics and interactions are logged for evaluation and debugging.
Interaction Metrics
Metrics are logged in metrics_summary.json and include:

Total actions performed
Successful and failed object identifications
Number of communication turns for both human and agent

Examples
Input:
Describe the object you're looking for (or type 'exit' to quit): red cup on the table
Output:
The agent explores the environment, identifies potential objects, and presents a confirmation image.

Metrics Example:
{
  "total_actions": 18,
  "successful_finds": 2,
  "failed_finds": 1,
  "communication_turns_human": 5,
  "communication_turns_agent": 12
}

Future Improvements
Enhance handling of ambiguous descriptions through better question-generation strategies.
Improve spatial relationship detection for complex environments.
Extend support for more diverse object attributes and user instructions.

References
AI2-THOR Documentation: https://ai2thor.allenai.org/
spaCy: https://spacy.io/
Transformers: https://huggingface.co/transformers/
