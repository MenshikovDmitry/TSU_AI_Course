# Homework 2
Object detection and segmentation.  
__DEADLINE:  you_know_when().date()__
### Task
It is a real life industry task. [This video](https://homeassistant.bramble1.duckdns.org/local/clodding_train.avi) contains the outcome from a clodding machine. It grinds the soil or rocks and turns them into equally-sized clods, which are passed to the next step in the production chain. When the clodding machine malfunctions, it produces abnormally big clods which may damage the next machine and disable the entire chain.  
Your task is to implement an online diagnostic system based on Computer Vision.  The customer wants the system to 
1) Detect abnormal clods 
2) Estimate the number of them in each frame
3) Estimate the size of the biggest one in the frame. 

![demo gif](example.png?raw=true "Pic")
--------------
### Requirements
We don't accept homework if any of the following requirements are not satisfied:
- The code should be situated in a public github (or gitlab) repository. Two branches: `dev` for development and `master` for the latest working version.
- All the necessary packages should be mentioned in `./requirements.txt`
- Sufficient `README.md` file:
    - Your credentials
    - "**How To**" for your repo: train model, evaluate, deploy.
    - Resources you utilized
- Your code must be fully covered with logging to `./data/log_file.log`. The file should be viewable and downloadable
- Proper `.gitignore` file. You do not want rubbish in your repo.
- The major software artifact is `model.py`, containing the class `<My_Rec_Model>` with following methods:
    - `train`. Recieves the dataset folder. Performs model training. Saves the artifacts to `./model/`. Logs the results.
    - `evaluate`. Recieves the dataset folder. Loads the model from `./data/model/`. Evaluates the model with the provided dataset, prints the results and saves it to the log.
    - `demo`. Runs real-time demo with provided image or video file.
- An integrated script for training and evaluation from CLI (check out `if __name__ == '__main__':`) so that:
```console
foo@bar:~$ python myfile.py train --dataset=/path/to/train/dataset
foo@bar:~$ python myfile.py evaluate --dataset=/path/to/evaluation/dataset
foo@bar:~$ python myfile.py demo the_video.avi 
```
### Dataset
Sorry, you are not provided with the dataset. It is called the real life, get used to it :-). You have a request from the potential customer and the video file. You are free to use any tools to achieve the goal and sell the project to the client. My suggestion is to combine your effort with the other students in creation of the sufficient dataset together.
The video is 33 seconds in length. Let's leave last 10 seconds for the evaluation purposes, it must not be used in training.  
You may want to implement a separate python module for the dataset purposes.

We are going to evaluate the models with two custom metrics:
- MSE of the number of abnormal clods
- MSE of the size of the biggest one
### Project Milestones
##### 1. Data Science
 1) The baseline object detector. Not necessary the segmentator. Must be implemented from scratch. 
 2) The Custom object Detector could be based on any repository or method.

##### 2. Engineering
At this point we expect to see fully working CLI application in the `master` branch.
Your goal is a pretty-looking demo for the Customer. You may want to store your model weights somewhere on the Internet for quick access.

### Grades
  
| Points | Bulletpoint     | Description                                                                                                                                                                                 |
|--------|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 10     | Dataset         | You managed to create a sufficient dataset both for object detection and object segmentation.                                                                                               |
| 20     | baseline model  | The model can detect the abnormal clods with the competitive metrics. The number is presented. No size estimation is required at this point. Speed does not matter. __Coded from scratch.__ |
| 10     | custom model    | Near to realtime detection. Competitive metrics. Number of abnormal clods is presented.                                                                                                     |
| 10     | size estimation | It is clearly seen in the demo which clod is the biggest in the frame. The size of the biggest one is presented.                                                                            
| 20     | model.py        | The model is properly packed into the class inside *.py file. CLI interface works well: train, evaluate, demo.                                                                              |
| 5      | git workflow    | Publicly available repo. dev and master branches. Regular Commits. No Commit Rush. Meaningful comment for each commit.                                                                      |
| 5      | nice repo       | User manual for using your code. Gif animation of your demo.                                                                                                                                
| 15     | Code quality    | Clear OOP pattern. Well in-code comments. Build-in documentation for each function. No code duplicates. Meaningful variable names                                                           |
| 5      | Logging         | Catch and log all possible errors. Singleton logging pattern (use logging module)                                                                                                           |


__Total: 100 points__ 

Enjoy your coursework!