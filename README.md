# Talk to Your Data: Building a Natural Language to SQL Generator 💬➡️💾

This project demonstrates how to build a system that converts natural language questions into executable SQL queries. It utilizes a powerful Large Language Model (LLM) via the Google Generative AI API (specifically, Gemini Pro) and LangChain to understand the user's question, interpret the database schema, and generate the corresponding SQL code.

The notebook showcases connecting to a local SQLite database, defining the database schema for the LLM, prompting the LLM with natural language questions, and receiving generated SQL queries.

**Database:** Example SQLite database (`Chinook.db`) containing music store data (artists, albums, tracks, customers, invoices, etc.).
**LLM:** Google Gemini Pro (accessed via Google Generative AI API)
**Framework:** LangChain (`SQLDatabaseChain`)
**Focus:** Demonstrating Natural Language Processing (NLP), LLM interaction for code generation (Text-to-SQL), database schema interpretation, and integrating these components using LangChain.
**Repository:** [https://github.com/Jayasurya227/Building-a-Natural-Language-to-SQL-Generator](https://github.com/Jayasurya227/Building-a-Natural-Language-to-SQL-Generator)

***

## Key Techniques & Concepts Demonstrated

Based on the analysis within the notebook (`15_Talk_to_Your_Data_Building_a_Natural_Language_to_SQL_Generator.ipynb`), the following key concepts and techniques are applied:

* **Natural Language Processing (NLP):** Understanding and processing human language queries.
* **Large Language Models (LLMs):** Utilizing Google Gemini Pro for its advanced language understanding and code generation capabilities.
* **Text-to-SQL:** The specific task of converting natural language questions about data into SQL queries.
* **Database Interaction:** Connecting to and querying a relational database (SQLite).
* **Schema Awareness:** Providing the LLM with information about the database structure (tables, columns, relationships) so it can generate accurate queries.
* **LangChain Framework:** Using LangChain's `SQLDatabaseChain` to orchestrate the interaction between the LLM, the database connection, and the user's natural language input.
* **Prompt Engineering (Implicit):** LangChain handles the prompt construction internally, but the process involves structuring the input (question + schema) effectively for the LLM.
* **API Integration:** Using the Google Generative AI API to access the Gemini Pro model.

***

## Analysis Workflow

The notebook follows a workflow typical for building a Text-to-SQL application:

1.  **Setup & Dependencies:**
    * Installing necessary libraries (`langchain`, `google-generativeai`, `python-dotenv`, etc.).
    * Importing required modules from LangChain, Google Generative AI, and standard libraries (like `sqlite3`, `os`).
2.  **API Key Configuration:** Loading the Google API key from environment variables (using `dotenv`).
3.  **Database Connection:**
    * Connecting to the local SQLite database (`Chinook.db`) using `sqlite3`.
    * (Alternative using LangChain's `SQLDatabase`): Creating an `SQLDatabase` object from a SQLAlchemy URI to allow LangChain to interact with the database.
4.  **LLM Initialization:** Initializing the Google Gemini Pro model (`ChatGoogleGenerativeAI`).
5.  **LangChain Setup (`SQLDatabaseChain`):**
    * Creating an `SQLDatabaseChain` instance, providing it with the initialized LLM and the `SQLDatabase` object. This chain encapsulates the logic for:
        * Inspecting the database schema.
        * Constructing a prompt for the LLM containing the schema and the user question.
        * Sending the prompt to the LLM.
        * Receiving the generated SQL query from the LLM.
        * (Optionally) Executing the query against the database and returning the result.
6.  **Querying:**
    * Defining natural language questions as input strings.
    * Running the questions through the `SQLDatabaseChain` (`chain.run("Your question here")`).
    * Printing the generated SQL query and/or the result obtained by executing the query.

***

## Technologies Used

* **Python**
* **LangChain:** Framework for building LLM applications, specifically `SQLDatabaseChain`.
* **Google Generative AI SDK (`google-generativeai`):** For interacting with the Google Gemini Pro LLM.
* **SQLAlchemy:** (Used internally by LangChain's `SQLDatabase`) For database abstraction.
* **SQLite (`sqlite3`):** For connecting to the example database.
* **python-dotenv:** For managing API keys securely.
* **Jupyter Notebook / Google Colab:** For the interactive development environment.

***

## Prerequisites

1.  **Google API Key:** You need an API key for Google Generative AI. You can obtain one from [Google AI Studio](https://aistudio.google.com/).
2.  **Chinook Database:** The `Chinook.db` SQLite database file must be present in the working directory. This is a common sample database and can be found online (e.g., [Chinook Database GitHub](https://github.com/lerocha/chinook-database)).
3.  **Environment Variable:** Store your Google API key in a `.env` file in the project directory with the key `GOOGLE_API_KEY`.
    ```
    GOOGLE_API_KEY="YOUR_API_KEY_HERE"
    ```

***

## How to Run the Project

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/Jayasurya227/Building-a-Natural-Language-to-SQL-Generator.git](https://github.com/Jayasurya227/Building-a-Natural-Language-to-SQL-Generator.git)
    cd Building-a-Natural-Language-to-SQL-Generator
    ```
2.  **Install dependencies:**
    (It is recommended to use a virtual environment)
    ```bash
    pip install langchain langchain_google_genai google-generativeai python-dotenv SQLAlchemy
    # Note: Depending on your setup, you might need specific DB drivers if not using SQLite
    ```
3.  **Set up Prerequisites:**
    * Download the `Chinook.db` file and place it in the repository root.
    * Create a `.env` file in the root directory and add your `GOOGLE_API_KEY`.
4.  **Launch Jupyter Notebook:**
    ```bash
    jupyter notebook "15_Talk_to_Your_Data_Building_a_Natural_Language_to_SQL_Generator.ipynb"
    ```
5.  **Run Cells:** Execute the cells sequentially. You can modify the example questions in the final cells to test the system with different natural language queries.

***

## Author & Portfolio Use

* **Author:** Jayasurya227
* **Portfolio:** This project ([https://github.com/Jayasurya227/Building-a-Natural-Language-to-SQL-Generator](https://github.com/Jayasurya227/Building-a-Natural-Language-to-SQL-Generator)) demonstrates cutting-edge NLP and LLM application skills by building a practical Text-to-SQL generator. It's highly relevant for showcasing abilities in AI, NLP, LLM integration, and database interaction. Suitable for GitHub, resumes/CVs, LinkedIn, and interviews targeting AI/ML Engineer, NLP Engineer, or Data Scientist roles.
* **Notes:** Recruiters can observe the use of modern tools like LangChain and Google's Generative AI to solve a complex problem – bridging the gap between human language and structured database queries. It highlights the ability to integrate different technologies to build intelligent data interaction systems.
