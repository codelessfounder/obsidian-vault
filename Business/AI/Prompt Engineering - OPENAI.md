---

---

Source:[https://platform.openai.com/docs/guides/prompt-engineering](https://platform.openai.com/docs/guides/prompt-engineering)



1. System messages 

Use a combination of system and user messages for more accurate LLM outputs

Example:

- Desired outcome: A response from the AI consisting only of emojis
- System message: “*You will be provided with a message, and your task is to respond using emojis only”*
- User message: “*How are you?”*

2. Example demonstration

Example:

- if you would like a document formatted in a certain way, provide a sample document for the LLM to use as a reference in its response

3. **Write clear instructions **

- * Include details in your query to get more relevant answers*

| Worse | Better |
| --- | --- |
| How do I add numbers in Excel? | How do I add up a row of dollar amounts in Excel? I want to do this automatically for a whole sheet of rows with all the totals ending up on the right in a column called "Total". |
| Who’s president? | Who was the president of Mexico in 2021, and how frequently are elections held? |
| Write code to calculate the Fibonacci sequence. | Write a TypeScript function to efficiently calculate the Fibonacci sequence. Comment the code liberally to explain what each piece does and why it's written that way. |
| Summarize the meeting notes. | Summarize the meeting notes in a single paragraph. Then write a markdown list of the speakers and each of their key points. Finally, list the next steps or action items suggested by the speakers, if any. |

- *Ask the model to adopt a persona*
Example: “
*When I ask for help to write something, you will reply with a document that contains at least one joke or playful comment in every paragraph.*
NB: the persona can be implicit or explicit


- *Use delimiters to clearly indicate distinct parts of the input *
example:
*summarise the texted delimited with triple quotes in a limerick:

"""cheese"""*

NB: XML tags and section titles can also be used to demarcate sections of text. These can be particularly useful for complex tasks to clarify task details. Don’t make the model work to understand exactly what you are asking of them.

- *Specify the steps required to complete a task *

Example:

- *Provide examples*
AKA “few-shot” prompting
This allows you to temporarily train the model to give you your desires output based on previous responses you give it, or it gives you. 
Example:
    1. *The movie was good // positive*
    2. *The movie was quite bad // negative*
    3. *I really like the movie, but the ending was lacking // neutral*
    4. *I LOVED the movie // ****(LLM will fill this in based on previous responses)***

SYSTEM
Answer in a consistent style.
USER
Teach me about patience.
ASSISTANT
The river that carves the deepest valley flows from a modest spring; the grandest symphony originates from a single note; the most intricate tapestry begins with a solitary thread.
USER
Teach me about the ocean.

- *Specify the desired length of the output*
NB: this does not work with precision and is generally limited to paragraphs or number of bullet points


4. **Provide reference text**

- *Instruct the model to answer with citations from a reference text *

A model can be instructed to provide an answer only from an inputted reference text with a supplementary citation to the location of the answer in the reference text.

Example:

SYSTEM
You will be provided with a document delimited by triple quotes and a question. Your task is to answer the question using only the provided document and to cite the passage(s) of the document used to answer the question. If the document does not contain the information needed to answer this question then simply write: "Insufficient information." If an answer to the question is provided, it must be annotated with a citation. Use the following format for to cite relevant passages ({"citation": …}).
USER
"""<insert document here>"""

Question: <insert question here>

5. **Split complex tasks into simpler subtasks**

- *Use intent classification to identify the most relevant instructions for a user query*
    - Route queries to predefined instructions to ensure relevant and efficient guidance.
    - Reduce redundant processing by only running necessary instructions instead of generic prompts.
    - Enable state tracking so the AI remembers past steps and avoids repetition.
    - Handle unexpected inputs by reclassifying queries when users switch topics.
    - Automate escalation by flagging unresolved issues for human support with context.
    - Improve efficiency by reducing computational costs through modular responses.
    - Enhance user experience by providing step-by-step structured guidance.
    - Ensure adaptability by dynamically adjusting instructions based on query classification.
    - Maintain logical flow so troubleshooting follows a clear sequence.
    - Prevent unnecessary detours by keeping AI responses focused and relevant.
    - Create a scalable system that allows AI to manage complex interactions with minimal intervention.

6. **Give the model time to “think”**

- *Instruct the model to work out its own solution before rushing to a conclusion *
Instruct the model to reason from *first principles* before coming to a conclusion. Asking a model if a maths equation is correct or not may yield varying results. 
Instead, prompt the model to generate its own solution first.

- *Ask the model if it missed anything on previous outputs *
If a model is asked to retrieve excerpts from a document, it must decide itself whether to write another excerpt or stop writing. If the document is large, it is common for a model to stop too early and miss all relevant excerpts.
    - at this point, you should prompt the model again with to make sure no excerpts were missed? 

Example:

*Are there more relevant excerpts? Take care not to repeat excerpts. Also ensure that excerpts contain all relevant context needed to interpret them - in other words don't extract small snippets that are missing important context.*

7. **Use external tools **

- *Use embeddings-based search to implement efficient knowledge retrieval*
It may be useful to add high quality information to a query relating to the query topic to improve the output 

- *Use code execution to perform more accurate calculations or call external APIs*
Example:
*You can write and execute Python code by enclosing it in triple backticks, e.g. ```code goes here```. Use this to perform calculations.*

If a model is provided with the documentation or code examples on how to use an API, a model can make use of that API. It can also write code (code execution)for calling an API.


8. **Test changes systematically **



Prompting libraries, tools and guides: [Related resources from around the web | OpenAI Cookbook](https://cookbook.openai.com/articles/related_resources)

Papers on advanced prompting to improve engineering: [Related resources from around the web | OpenAI Cookbook](https://cookbook.openai.com/articles/related_resources)



**Supplementary Prompt for Optimal LLM Responses:**

- **Clarify the task:** Specify the desired outcome, format, length, or response style.
- **Provide examples:** Include a few relevant samples for consistency.
- **Use precise language:** Avoid ambiguity by detailing key aspects.
- **Break down complex tasks:** If needed, outline clear steps.
- **Reference supporting materials:** Provide relevant text, links, or context for accuracy.
- **Specify persona or tone:** If applicable, instruct the model to respond in a particular style.
- **Encourage step-by-step reasoning:** For complex queries, ask the model to think through its response before concluding.
- **Use delimiters for clarity:** Clearly separate different sections of input when necessary.

I completed a project with 100% AI-generated code as a technical person. Here are quick 12 lessons

Using Cursor & Windsurf with Claude Sonnet, I built a NodeJS & MongoDB project - as a technical person.

**1- Start with structure, not code**

The most important step is setting up a clear project structure. Don't even think about writing code yet.

**2- Chat VS agent tabs**

I use the chat tab for brainstorming/research and the agent tab for writing actual code.

**3- Customize your AI as you go**

Create "Rules for AI" custom instructions to modify your agent's behavior as you progress, or maintain a [RulesForAI.md](http://rulesforai.md/) file.

**4- Break down complex problems**

Don't just say "Extract text from PDF and generate a summary." That's two problems! Extract text first, then generate the summary. Solve one problem at a time.

**5- Brainstorm before coding**

Share your thoughts with AI about tackling the problem. Once its solution steps look good, then ask it to write code.

**6- File naming and modularity matter**

Since tools like Cursor/Windsurf don't include all files in context (to reduce their costs), accurate file naming prevents code duplication. Make sure filenames clearly describe their responsibility.

**7- Always write tests**

It might feel unnecessary when your project is small, but when it grows, tests will be your hero.

**8- Commit often!**

If you don't, you will lose 4 months of work like this guy \[[Reddit post](https://www.reddit.com/r/cursor/comments/1inoryp/cursor_fck_up_my_4_months_of_works/)\]

**9- Keep chats focused**

When you want to solve a new problem, start a new chat.

**10- Don't just accept working code**

It's tempting to just accept code that works and move on. But there will be times when AI can't fix your bugs - that's when your hands need to get dirty (main reason non-tech people still need developers).

**11- AI struggles with new tech.**

When I tried integrating a new payment gateway, it hallucinated. But once I provided docs, it got it right.

**12- Getting unstuck**

If AI can't find the problem in the code and is stuck in a loop, ask it to insert debugging statements. AI is excellent at debugging, but sometimes needs your help to point it in the right direction.

While I don't recommend having AI generate 100% of your codebase, it's good to go through a similar experience on a side project, you will learn practically how to utilize AI efficiently.

\* It was a training project, not a useful product.

For more useful content, connect with me on [LinkedIn](https://www.linkedin.com/in/qaishweidi), even though I don't like it much.


