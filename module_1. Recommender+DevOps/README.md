# Homework 1 
Recommender System + DevOps Essentials.
__DEADLINE:  --.--.2025__
### Task
Implement and deploy a production-ready recommender system.
The current homework consists of two parts: The Data Science Part and The DevOps Essentials.
Firstly, you need to train a competitive recommender system, and secondly: wrap your code into a production-ready artifact, which may be deployed on any Linux server in one command.
### Before we start 
Data science is an industry that is fully based on tons of open source tools, supported by a wide community. Whenever you, as a Data Scientist, train a model in the Jupyter environment, you have to understand that this moment is only a starting point in the lifecycle of the model, which is assumed to be deployed on the production server. On **Linux** Server. Hiring a Junior DS, I prefer one with at least basic Linux exposure and Command Line Interface (_CLI_) experience.
###### Linux users:
:thumbsup:
###### Windows users:
You can deal with the Data Science part of this homework, sitting on Windows and using Colab. However, you may struggle with the DevOps part when you reach Docker and docker-compose. I do encourage you to consider having Linux as a second operating system on your machine. Check out Ubuntu 24.04, it is friendly enough.
###### Mac users:
Mac OS has a FreeBSD core in its heart and in general, it is much closer to Linux than Windows. Lots of DS and DE use Mac. I personally not a Mac user, so I can not support you in case of issues. I will do my best though.

--------------
### Requirements
We don't accept homework if any of the following requirements are not satisfied:
- The code should be situated in a public github (or gitlab) repository. Two branches: `dev` for development and `master` for the latest working version.
- project dependancies are managed with [poetry](https://python-poetry.org/)
- Sufficient `README.md` file:
    - Your credentials
    - "**How To**" for your repo: Set up the environment, train the model, evaluate, deploy. With and without docker.
    - Resources you utilized
- Your code must be fully covered with logging to `./data/log_file.log`. The file should be viewable and downloadable
- Proper `.gitignore` file. You do not want rubbish in your repo.
- The major software artifact is `model.py`, containing the class `My_Rec_Model` with following methods:
    - `train`. Recieves the dataset filename. Performes model training. Saves the artifacts to `./model/`. Logs the results.
    - `evaluate`. Recieves the dataset filename. Loads the model from `./data/model/`. Evaluates the model with the provided dataset, prints the results and saves it to the log.
    - `predict`. Recieves list `[[movie_id_1, movie_id_2, .., movie_id_N ], [rating_1, rating_2, .., rating_N]]` and returns TOP M (also a parameter) recommended movies with estimated rating in the same as input format.
    - `warmup`. Loads the model from `./data/model/`. Refreshes the model if it is already loaded.
    - `find_similar`. Returns N (parameter, default=5) most similar movies for input `movie_id`. Returns list `[[movie_id_1, movie_id_2, .., movie_id_N ], [[movie_name_1, movie_name_2, .., movie_name_N]]]` Descending sorting by similarity.
- An integrated script for training and evaluation from CLI (check out `if __name__ == '__main__':`) so that:
```console
foo@bar:~$ python model.py train --dataset=/path/to/train/dataset
foo@bar:~$ python model.py evaluate --dataset=/path/to/evaluation/dataset
foo@bar:~$ python model.py predict --dataset=/path/to/evaluation/dataset
```
- Checkout [fire.fire](https://github.com/google/python-fire). It might help you to create the CLI app. It is too good to be true :).
- Flask Application (feel free to use FastAPI or other frameworks) `flask_app.py`. Runs REST API service on port 5000. 
 - `Dockerfile`
- `docker-compose.yaml`
- CI/CD script for github or gitlab
### Dataset
I hope you like movies. We are going to use [MovieLens](https://grouplens.org/datasets/movielens/) dataset. Please find train and test data in the `dataset` folder of this repo. There are also some supplemental data avialable such as User and movies metadata. You may or may not use it in your project. 

### Project Milestones
##### 1. Data Science in Jupyter
Feel free to stick to Jupyter or Colab environment. Here we expect you to build two movie recommender models. 
 1) A baseline recommender build on Collaborative filtering and matrix factorization of your choice.  You are only allowed to use standard python packages including pandas, numpy, sklearn, etc.  
 2) Custom Recommender based on the method of your choice.

For both tasks, please, refer to target metrics at the end of current README.

##### 2. Pack into git repo
At this point we expect to see fully working CLI application in the `master` branch
##### 3. REST API interface fith `Flask`
Serving on port 5000. Do not forget to catch and log Error 500. It is a good Idea to test your API from Jupyter Notebook with `requests` module.
Endpoints:
- `/api/predict`. Recieves list `[[movie_name_1, movie_name_2, .., movie_name_N ], [rating_1, rating_2, .., rating_N]]` and returns TOP M (default 20, also a parameter) recommended movies with corresponding estimated rating. Sort descending. `[[movie_name_1, movie_name_2, .., movie_name_M], [rating_1, rating_2, .., rating_M]]`
- `/api/log`. Last 20 rows of log.
- `/api/info`. Service Information: Your Credentials, Date and time of the build of the Docker image, Date, time and metrics of the training of the currently deployed model.
- `/api/reload`. Reload the model.
- `/api/similar`. returns list of similar movies `{"movie_name": "Lord of the Rings"}`  
  
 Please, Note, that API call contains movie names, not IDs. You must handle this on the server side.  
Expose the port with ngrok, so I could play around with your APIs at the final practice session
##### 4. Docker and docker-compose
Docker basically locks your application inside the virtual environment called a container, containing the necessary dependencies. The container wipes everything after the restart. You do not want to pack the model artifacts to the docker image. Instead, map the local folder "data" with corresponding folder inside the container. Keep the artifacts like model data and log file persistent.
- remember to expose port 5000
- map 5000 port of the container and 5000 (or any other) of your machine
- map 'data' folders
 
Create a `docker-compose.yaml` file, so that you can start the service in a single command
```console
foo@bar:~$ docker-compose up --build
```
Which builds docker image and spins up container with the necessary parameters.
    
##### 4. CI/CD
Continious Integration / Continious Delivery.  
It is annoying to manually rebuild and restart your service after each bugfix. Thats why people automate it. Use `Github Actions` or `Gitlab CI` to rebuild the docker image every time the new commit or merge affects the `master` branch.
- Build Docker image
- Refresh info file
- push the image to the Docker Registry. _(!Do not place your login/password data to the repository. Use `Secrets` instead!)_  

If those steps are completed, I do not need to take care of the dependencies and environment to run your service. All I need is to pull your image, download the model artifacts and spin up the container.

##### 5. Grades
###### 5.1 Data Science part  
| Points         | RMSE     | Description |
|--------------|-----------|------------|
| 0       | > 1      |    Mean user rating gives this value of RMSE     |
| 20      | < 0.95  | Baseline with Matrix Factorisation. Compulsory for everyone.       |
| 10      | < 0.9  | Doable       |
| 10      | < 0.85  | SOTA-ish without features       |
| 10      | < 0.83  | Close to SOTA       |  


__Total: 50 points__  
Please, note that cheating with metrics will lead you to the grade 0.

###### 5.2 DevOps part  
  
| Points         | Bulletpoint     | Description |
|--------------|-----------|------------|
| 15     | model.py      |    The model is properly packed into the class inside *.py file. CLI interface works well: train, evaluate, predict.      |
| 5      | git workflow  | Publicly available repo. dev and master branches. Regular Commits. No Commit Rush. Meaningful comment for each commit.        |
| 10     |Code quality   | Clear OOP pattern. Well in-code comments. Build-in documentation for each function. No code duplicates. Meaningful variable names       |
| 5      | Logging       |Catch and log all possible errors. Singleton logging pattern (use logging module)      |
| 5      | REST API      | Working API with Flask and **WSGI**. Endpoints according to description above. Catch and log 500       |
| 3      | docker        | working API in a docker container. Shared folder for all the artifacts (model files, logs)      |
| 2      |docker-compose | working docker-compose file       |
| 5      | CICD          | working actions file. merge or commit to master -> build and push docker image to dockerhub       |  


__Total: 50 points__ 

### Useful Resources
- [PyCharm: Python IDE](https://www.jetbrains.com/pycharm/)
- [Markdown Editor](https://dillinger.io/)
- [MovieLens Data Exploration](https://github.com/Lal4Tech/movielens-data-exploration/blob/master/src/main/code/exploratory_analysis.ipynb)
