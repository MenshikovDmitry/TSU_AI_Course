# Homework 4
GPT-Telegram Bot & RAG.  
*RAG = Retrieval-Augmented Generation.  
  
__DEADLINE:__  you_know_when()  
### Task
Do you like ChatGPT? I know you do!  
This time you will create your very own ChatGPT-sort of bot for Telegram.  
We will make it useful. We will teach it to answer the questions based on some actual set of documents. Let's help schoolies with their homework! The bot will help answering "exam" questions about the book "Master and Margarita" by Mikhail Bulgakov. You can find it in this repo. Feel free to choose any other book or set of documents.  
[Here](https://kladraz.ru/viktoriny/voprosy-k-romanu-master-i-margarita-11-klas-s-otvetami.html?ysclid=lwsgltzmcp930457617) are some exam questions for you to start with.  
I used [this](https://github.com/aiogram/aiogram) library for the telegram bot, but you are free to choose any other.

--------------
### Requirements
We don't accept homework if any of the following requirements are not satisfied:
- The code should be situated in a public github (or gitlab) repository. Two branches: `dev` for development and `master` for the latest working version.
- All the necessary packages should be mentioned in `./requirements.txt`
- Sufficient `README.md` file:
    - Your credentials
    - "**How To**" for your repo: train model, evaluate, deploy if applicable.
    - Resources you utilized
- Your code must be fully covered with logging to `./data/log_file.log`. The file should be viewable and downloadable
- Proper `.gitignore` file. You do not want rubbish in your repo.
- **<span style="color: red;">Your model MUST BE Fully CLI - enabled. No Jupyter Notebooks allowed this time.</span>**

### Project Milestones
##### 1. Search Engine and Indexer
You must spin-up a local search engine for the documents. It must be able to search for the documents and quotes based on the user query. How about containerized Elasticsearch? You must be able to index documents and retrieve them with Python CLI. Do not forget the text normalization and stemming.

##### 2. RAG  
Add "AI"-ness to your search engine with third-party LLM API's. Thus, you can "ask" your cli app a question, it will find relevant entries in the documents and will generate the answer to the question based on the search results. Your app must provide a quote of the original text.

##### 3. Add a bot
Now you can wrap your app into a Telegram bot. It must be able to store the context of the conversation with **each** user. Your bot must say "I don't know", or "the question is irrelevant" in case it can't find the answer.

### Grades
  
| Points | Bulletpoint                                  | Description                                                                                                                                      |
|--------|----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| 10     | Your Search Engine is up and running         | You can index and retrieve documents with python. Text normalization and stemming are in place.                                                  |
| 15     | RAG is up                                    | You can query your app with "human-like" questions. It queries the SE and generates the answer in a "human-like" way. It provides quote.         |
| 15     | Telegram GPT-Bot                             | You can chat with your app. I can chat with your bot. Everyone can. It stores conversation context for multiple users.                           |
| 15     | Separate documents collection for each users | every user has its own set of documents.                                                                                                         |                                                                             
| 10     | Fully independant workflow in telegram bot   | User level: Add documents, search, ask questions, get answers & quotes; drop the entire collection.                                              |                                                                                                              
| 5      | app.py                                       | The project is properly packed into the class inside *.py file. CLI interface works well: train, evaluate, demo if applicable.                   |
| 5      | git workflow                                 | Publicly available repo. dev and master branches. Regular Commits. No Commit Rush. Meaningful comment for each commit.                           |
| 5      | nice repo                                    | User manual for using your code. Gif animation of your demo.                                                                                     
| 15     | Code quality                                 | Readable code. Clear OOP pattern. Well in-code comments. Build-in documentation for each function. No code duplicates. Meaningful variable names |
| 5      | Logging                                      | Catch and log all possible errors. Singleton logging pattern (use logging module)                                                                |

**!Bounty!** extra 10 points for implementing an **option of** a vector search in your search engine. How about Word2Vec / FastText / Bert / Others? 

__Total: 100 points__ 

Enjoy your coursework!