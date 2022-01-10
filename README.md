# Homework 1 
Recommendation System + DevOps Essentials.
### Task
Implement and deploy a production-ready recommendation system.
The current homework consists of two parts: The Data Science Part and The DevOps Essentials.
Firstly, you need to train a competitive recommendation system, and secondly: wrap your code into a production-ready artifact, which may be deployed on any Linux server in one command.
### Before we start 
Data science is an industry that is fully based on tons of open source tools, supported by a wide community. Whenever you, as a Data Scientist, train a model in the Jupyter environment, you have to understand that this moment is only a starting point in the lifecycle of the model, which is assumed to be deployed on the production server. On **Linux** Server. Hiring Junior DS, I always prefer ones with at least basic Linux exposure and Command Line Interface (_CLI_) experience.
###### Linux users:
:thumbsup:
###### Windows users:
You can deal with the Data Science part of this homework, sitting on Windows and using Colab. However, you may struggle with the DevOps part when you reach Docker and docker-compose. I do encourage you to consider having Linux as a second operating system on your machine. Check out Ubuntu 20.04, it is friendly enough.
###### Mac users:
Mac OS has a FreeBSD core in its heart and in general, it is much closer to Linux than Windows. Lots of DS and DE use Mac. I personally not a Mac user, so I can not support you in case of issues. I will do my best though.

--------------
### Requirements
We don't accept homework if any of the following requirements are not satisfied:
- The code should be situated in a public github (or gitlab) repository. Two branches: `dev` for development and `master` for the latest working version.
- All the necessary packages should be mentioned in `./requirements.txt`
- Sufficient `README.md` file:
    - Your credentials
    - "**How To**" for your repo: train model, evaluate, deploy. With or without docker.
    - Resources you utilized
- Your code must be fully covered with logging to `./data/log_file.log`. The file should be viewable and downloadable
- Proper `.gitignore` file. You do not want rubbish in your repo.
- The major software artifact is `model.py`, containing the class `My_Rec_Model` with following methods:
    - `train`. Recieves the dataset filename. Performes model training. Saves the artifacts to `./model/`. Logs the results.
    - `evaluate`. Recieves the dataset filename. Loads the model from `./data/model/`. Evaluates the model with the provided dataset, prints the results and saves it to the log.
    - `predict`. Recieves list `[[movie_id_1, movie_id_2, .., movie_id_N ], [rating_1, rating_2, .., rating_N]]` and returns TOP M (also a parameter) recommended movies with estimated rating in the same as input format.
    - `warmup`. Loads the model from `./data/model/`.
- A helping script for training and evaluation from CLI (you may integrate it into `model.py`) so that:
```console
foo@bar:~$ python model.py train --dataset=/path/to/train/dataset
foo@bar:~$ python model.py evaluate --dataset=/path/to/evaluation/dataset
foo@bar:~$ python model.py predict --dataset=/path/to/evaluation/dataset !!!!FORMAT
```
- Flask Application `flask_app.py`. Runs REST API service on port 5000. 
 - `Dockerfile`
- `docker-compose.yaml`
- CI/CD script for github or gitlab
### Dataset
!!!TO BE DONE !!!

### Project Milestones
##### 1. Data Science in Jupyter
!!DESCRIBE Methods, SOTAS ETC!!!
##### 2. Pack into git repo
At this point we expect to see fully working CLI application
##### 3. REST API interface fith `Flask`
Serving on port 5000. Do not forget to catch and log Error 500. It is a good Idea to test your API from Jupyter Notebook with `requests` module.
Endpoints:
- `/predict`. Recieves list `[[movie_id_1, movie_id_2, .., movie_id_N ], [rating_1, rating_2, .., rating_N]]` and returns TOP M (default 20, also a parameter) recommended movies with corresponding estimated rating. Sort descending. `[[movie_name_1, movie_name_2, .., movie_name_M], [rating_1, rating_2, .., rating_M]]`
- `/api/log`. Last 20 rows of log.
- `/api/info`. Service Information: Your Credentials, Date and time of the build of the Docker image, Date, time and metrics of the training of the currently deployed model.
##### 4. Docker and docker-compose
Docker basically locks your application inside the virtual environment called a container, containing the necessary dependencies. The container wipes everything after the restart. You do not want to pack the model artifacts to the docker image. Instead, map the local folder "data" with corresponding folder inside the container. Keep the artifacts like model data and log file persistant.
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




### Useful Resources
- [PyCharm: Python IDE](https://www.jetbrains.com/pycharm/)
- [Markdown Editor](https://dillinger.io/)
