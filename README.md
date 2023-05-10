# ChatGPT Prompt Engineering for Developers
Jupyter code notebooks of "ChatGPT Prompt Engineering for Developers" by DeepLearning.AI and OpenAI.

In ChatGPT Prompt Engineering for Developers, you will learn how to use a large language model (LLM) to quickly build new and powerful applications.  Using the OpenAI API, you’ll be able to quickly build capabilities that learn to innovate and create value in ways that were cost-prohibitive, highly technical, or simply impossible before now.

This short course taught by Isa Fulford (OpenAI) and Andrew Ng (DeepLearning.AI) will describe how LLMs work, provide best practices for prompt engineering, and show how LLM APIs can be used in applications for a variety of tasks, including:

- Summarizing (e.g., summarizing user reviews for brevity)
- Inferring (e.g., sentiment classification, topic extraction)
- Transforming text (e.g., translation, spelling & grammar correction)
- Expanding (e.g., automatically writing emails)

In addition, you’ll learn two key principles for writing effective prompts, how to systematically engineer good prompts, and also learn to build a custom chatbot. 

All concepts are illustrated with numerous examples, which you can play with directly in our Jupyter notebook environment to get hands-on experience with prompt engineering. 

## Few Extract from the notebooks:

### Prompting Principles

	1. GUIDELINES:

	Principle 1: Write clear and specific instructions
	Tactic 1: Use delimiters to clearly indicate distinct parts of the input
	Tactic 2: Ask for a structured output
	Tactic 3: Ask the model to check whether conditions are satisfied
	Tactic 4: "Few-shot" prompting by providing 1 set of example
	
	Principle 2: Give the model time to “think”
	Tactic 1: Specify the steps required to complete a task
	Tactic 2: Instruct the model to work out its own solution before rushing to a conclusion

	2. ITERATIVE PROMPTS:
	
	Issue 1: The text is too long - Limit the number of words/sentences/characters.
	Issue 2. Text focuses on the wrong details - Ask it to focus on the aspects that are relevant to the intended 	 audience.
	Issue 3. Description needs a table of dimensions - Ask it to extract information and organize it in a table.
	
	Longer prompts are fine, explain each task step by step for the LLM to perform.
	Eg.,
	prompt = f"""
	Your task is to help a marketing team create a 
	description for a retail website of a product based 
	on a technical fact sheet.
	
	Write a product description based on the information 
	provided in the technical specifications delimited by 
	triple backticks.
	
	The description is intended for furniture retailers, 
	so should be technical in nature and focus on the 
	materials the product is constructed from.
	
	At the end of the description, include every 7-character 
	Product ID in the technical specification.
	
	After the description, include a table that gives the 
	product's dimensions. The table should have two columns.
	In the first column include the name of the dimension. 
	In the second column include the measurements in inches only.
	
	Give the table the title 'Product Dimensions'.
	
	Format everything as HTML that can be used in a website. 
	Place the description in a <div> element.
	
	Technical specifications: ```{fact_sheet_chair}```
	"""

	3. Summarizing:
		1. Summarize with a word/sentence/character limit
		2. Summarize with a focus on <"key words"> (eg., shipping and delivery)
		3. Summarize with a focus on price and value
		4. Try "extract" instead of "summarize"
	
	4. INFERRING:

	You will infer sentiment and topics from text,
	Sentiment (positive/negative)
	Identify types of emotions
	Extract key info from text
	Doing multiple tasks at once
	Eg., Identify the following items from the review text: 
	- Sentiment (positive or negative)
	- Is the reviewer expressing anger? (true or false)
	- Item purchased by reviewer
	- Company that made the item

	5. Transforming:
	Language Translation
	Tone Transformation(Formal to Informal)
	Format Conversion (JSON to HTML)
	Spellcheck/Grammar check

	6. Expanding:
	you will generate customer service emails that are tailored to each customer's review

	Customize the automated reply to a customer email
	Eg., prompt = f"""
	You are a customer service AI assistant.
	Your task is to send an email reply to a valued customer.
	Given the customer email delimited by ```, \
	Generate a reply to thank the customer for their review.
	If the sentiment is positive or neutral, thank them for \
	their review.
	If the sentiment is negative, apologize and suggest that \
	they can reach out to customer service. 
	Make sure to use specific details from the review.
	Write in a concise and professional tone.
	Sign the email as `AI customer agent`.
	Customer review: ```{review}```
	Review sentiment: {sentiment}
	"""
	Remind the model to use details from the customer's email

	temperature 
	In general, when building applications where you want a kind of predictable response, I would recommend using temperature zero.
	If you're trying to build a system that is reliable and predictable, you should go with 0. If you're trying to kind of use the model in a more creative way where you might kind of want a kind of wider variety of different outputs, you might want to use a higher temperature.
	So, to summarise, at higher temperatures, the outputs from the model are kind of more random. You can almost think of it as that at higher temperatures, the assistant is more distractible, but maybe more creative.
