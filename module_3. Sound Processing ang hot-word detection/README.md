# Homework 3
Sound Processing and hot-word detection.
__DEADLINE:  you_know_when__
### Task
No one expected the Infinity War to start that fast. Thanos is on the halfway to having all infinity 
stones collected, which have an incredible power as for creation as for total annihilation. He fancies himself a God and 
plans to destroy few worlds to 'save' the universe from overpopulation.  The Avengers' mission is to prevent him from doing that.
The Guardians of the Galaxy have found the secret 
  vault, where Ronan keeps the stones for Thanos. They also spotted a secret communication channel used by Ronan to transmit 
the access keys. They even managed to intercept one of the ciphered messages. It contains 5 code words which are the keys to the  stones' vault.   
Your missions are:
- Parse the intercepted message and extract all 5 access codes.
- Intercept the transmission and extract another 5 ones.

The pass codes are structured as follows:
- "hot-word":  STONES is followed by one of the secret keys.
- hot-word is 1 second length
- secret word follows the hot word after 200 milliseconds delay;
- secret word is always less than 1 second.

You are required to 
1) Collect a dataset, implement a hot-word detector and spot the secret words in the wav file 
2) Implement a service to listen to the broadcast and spot the rest secret words.
  
[wav file](https://disk.yandex.ru/d/Id76lvfCOw5Kbw) Example: first secret word could be spotted at 33:27.  
[Test Broadcast](https://radio.maslovka-home.ru/soundcheck) is available 24/7. Does NOT contain secret words. Consists of the same source files.  
[Real Broadcast](http://radio.maslovka-home.ru/thanosshow) Works only once each night 4am GMT+7.  
Guys, this is my private home server, please, do not DDOS it. I also kindly remind you that it is not a penetration testing coursework ;-).  

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

### Dataset
No dataset is provided this time. The only thing we know is that the hot-word is 'STONES'.
My suggestion is to collaborate and create your own dataset of 1 second-length files. [HERE](https://disk.yandex.ru/d/6B0vPmB52BEMqw) you 
can find hot words used in transmission. 

### Hints
- [Audacity](https://www.audacityteam.org/) is a nice open source sound manipulation tool.
- Let's use samplerate = 16000

### Project Milestones
##### 1. Create Dataset
##### 2. Hot-word detector
Must be implemented from scratch. Feel free to use standard tools such as librosa, numpy, keras, pytorch etc. 
However, you are not allowed to use ready-made hot-word detectors. There are only 10 secret words. STT model is not required.
##### 2. Broadcast interceptor
Connect to the stream and try to process it in real time to detect the rest of the access codes.

### Grades
  
| Points | Bulletpoint                                     | Description                                                                                                                                      |
|--------|-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| 10     | Dataset                                         | You have a sufficient dataset.                                                                                                                   |
| 25     | Your model is able to parse the long *.wav file | Your detector catches all 5 words. Exact time of appearance is reflected. The fragments of interest are saved locally.                           |
| 10     | Intersept the transmission and save it locally  | Your have implemented a service to wait and record the broadcast.                                                                                |
| 25     | Hot-word detector **service**                   | Your service is able to run in an autonomous manner, detect the broadcast and process it in real-time. Another 5 words are collected.            |
| 5      | module.py                                       | The model is properly packed into the class inside *.py file. CLI interface works well: train, evaluate, demo if applicable.                     |
| 5      | git workflow                                    | Publicly available repo. dev and master branches. Regular Commits. No Commit Rush. Meaningful comment for each commit.                           |
| 5      | nice repo                                       | User manual for using your code.                                                                                                                 
| 10     | Code quality                                    | Readable code. Clear OOP pattern. Well in-code comments. Build-in documentation for each function. No code duplicates. Meaningful variable names |
| 5      | Logging                                         | Catch and log all possible errors. Singleton logging pattern (use logging module)                                                                |


__Total: 100 points__ 

Enjoy your coursework!