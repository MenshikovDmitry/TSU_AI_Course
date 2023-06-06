# Homework 4
Text Sumarization & GPT-Bot  
__DEADLINE:__  you_know_when()  
### Task
Do you like ChatGPT? I know you do!  
This time you will create your very own ChatGPT-sort of bot for Telegram.  
You are required to implement the summarization plugin for it. 

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
##### 1. Simple Summarizer
The text summarizer based on approach, [introduced by H.P. Luhn](https://courses.ischool.berkeley.edu/i256/f06/papers/luhn58.pdf) in 1958 th must be implemented from scratch.  
This method is fully heuristic and does not linked to any particular dataset. Thus, it should not be a big deal for you to make the model multilingual. Let's say for English and Russian languages. Feel free to implement more. It is assumed that a document is written in only one dominant language (no multi-language documents). 
Your model must use stemming. You are allowed to use third-party libraries for it.
##### 2. Telegram GPT-Bot  
Your bot must behave similar to famous ChatGPT, but in telegram messenger. Come up with a nice name for it. It __must store the context__ of the dialog for __each__ user. Think about the way to wipe the context if the user wants to start the dialog from scratch. Obviously, you are allowed to use third-party API calls ;-). 

##### 3. Add plugins to the bot
It is LLM, so it has decent summarization skills "out of the box", however, when the user asks specifically for the Luhn summarization, It must be done using your plugin with __seamless user experience__.  
Your plugin must be implemented within a __framework__, so that later on you could add other plugins (say database query, image generation, or any other brilliant ideas you may come up with)
### Grades
  
| Points | Bulletpoint                                        | Description                                                                                                                                                 |
|--------|----------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 15     | Text summarizer for single language of your choice | `foo@bar:~$ python your_module.py document.txt` must generate the file `document_abstract.txt` with a summarization. Your summarizer must contain stemming. |
| 10     | Multilingual summarizer with language detection    | Exactly the same as the previous one. Must support at least 2 languages. Must detect the language of the document automatically.                            |
| 15     | Telegram GPT-Bot                                   | You can chat with your bot. I can chat with your bot. It stores context for multiple users.                                                                 |
| 15     | Plugins framework                                  | Your bot supports plugins. One of them: Luhn summarization. It works.                                                                                                  
| 10     | Another plugin                                     | Cool! you bot bot generates images.                                                                                                                          
| 5      | app.py                                             | The project is properly packed into the class inside *.py file. CLI interface works well: train, evaluate, demo if applicable.                              |
| 5      | git workflow                                       | Publicly available repo. dev and master branches. Regular Commits. No Commit Rush. Meaningful comment for each commit.                                      |
| 5      | nice repo                                          | User manual for using your code. Gif animation of your demo.                                                                                                
| 15     | Code quality                                       | Readable code. Clear OOP pattern. Well in-code comments. Build-in documentation for each function. No code duplicates. Meaningful variable names            |
| 5      | Logging                                            | Catch and log all possible errors. Singleton logging pattern (use logging module)                                                                           |


__Total: 100 points__ 

Enjoy your coursework!