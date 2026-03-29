# optimised_LLMs-
Optmised LLMs based for google's  gemma3 4B model, using ollama for creating various personas fo different workspaces,
using varioud factors such as -

1. Top-K (The Hard Limit)

Top-K limits the model's choices to a fixed number of the most likely next tokens.
  
How it works: If $K=20$, the model only looks at the top 20 most probable words and ignores everything else, no matter how close the 21st word might be in probability. 

Impact: A low $K$ (e.g., 5) makes the model very focused and predictable; a high $K$ (e.g., 50+) allows for more diverse vocabulary.

2. Top-P (Nucleus Sampling)

Top-P (or "Max P" logic) selects tokens based on their cumulative probability.

How it works: Instead of a fixed count like Top-K, it adds up the probabilities of the most likely words until they reach the threshold $P$ (e.g., 0.95 or 95%). 

Impact: This is more "dynamic" than Top-K. If the model is very confident, it might only look at 2 words. If it's unsure, it might look at 100 words to reach that 95% total.

3. Min-P (The Scalable Filter)

Min-P is a newer, more sophisticated alternative to Top-P. It filters out tokens that are not at least a certain percentage as likely as the most probable token.

How it works: If your $Min-P$ is $0.05$ and the top token has a 40% chance of being next, any token with less than a 2% chance ($0.05 \times 40\%$) is discarded.

Impact: This preserves creative "long-shot" options when the model is uncertain but aggressively cuts out nonsense when the model is highly confident.

# Why these specific  combinations?

1.The "Zero-Logic" Combo (Coding/Math)

Effect: Setting Temperature to 0.0 makes the model deterministic (it will likely give the same answer to the same prompt every time). Adding a small Min-P ensures that even if the model is "forced" to choose a second-best token, that token must still be statistically relevant. This prevents syntax errors in code.

2.The "Natural Professional" Combo (Email/Reports)

Effect: A low temperature keeps the tone professional, but the Repeat Penalty is slightly higher than default. This forces the model to use a wider vocabulary so it doesn't start every sentence with "Additionally..." or "Furthermore..."

3.The "Creative genius" Combo (Brainstorming)

Effect: High temperature usually makes a model "hallucinate" or talk nonsense. However, by pairing it with a high Min-P , you tell the model: "Be as creative as you want, BUT don't pick any word that is less than 10% as likely as the best word." This results in high-quality, surprising ideas that still make sense.

# The models -

1.Ron - "Zero-Logic" Combo (Coding/Math) - work/school
2.Gwen - "Creative genius" Combo (Brainstorming) - innovative ideas/work
3.jay - "Natural Professional" Combo (Email/Reports) - office/school
