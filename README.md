# GAI-project
import openai

# Replace with your OpenAI API key
openai.api_key = "YOUR_API_KEY"

def explain_experiment(experiment_name):
    prompt = f"""
    You are a science teacher. Explain the experiment titled '{experiment_name}'
    in a structured format with the following sections:
    1. Aim
    2. Materials Required
    3. Theory / Principle
    4. Procedure
    5. Observations
    6. Result
    7. Precautions
    Make it suitable for school or college students.
    """

    # Sending request to GPT model
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )

    explanation = response['choices'][0]['message']['content']
    return explanation


# Example usage
experiment = input("Enter the experiment name: ")
output = explain_experiment(experiment)
print("\n--- Generated Experiment Explanation ---\n")
print(output)
