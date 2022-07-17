## Intelligent Crime Reporting and Intervention System 
This project was done as a participation project for [Smart India Hackathon 2022](sih.gov.in).

## Problem Statement
- Create a system for citizens to report crimes anonymously while also giving the authorities a swift way to interfere

## Solution

Actual Summary : We made an uber for crimes with face detection and NLP to help investigation and an Admin Dashboard for quick information with a hint of smart contract in there to anonymously reward reporters with cryto currency

Let us go through the solution from a bottom up perspective i.e, from the **citizens**
1) They are provided with a mobile app for anonymous crime reporting along with the ability to upload media and exact location of where the crime has occured 

2) Other Features of the app include
    - Available in regional languages to reach a wider audience 
    - An emergency button to alert the authorities allowing you to broadcast your location in real time
 3) Tech Stack :- **Flutter** with BLOC State Management(Android + iOS) 
 
 4) [Github Repository Link](https://github.com/srikharshashi/citizensapp)
 
 5) [Play Store Link]()
 
 6) Screen Shots
 ---
![image](https://user-images.githubusercontent.com/37980605/179389499-5d3868db-8136-41ef-b578-35c872375798.png)
![image](https://user-images.githubusercontent.com/37980605/179388819-7b761657-32ad-4fe4-adda-9faf583c13f1.png)


Once the case has been reported by the citizens it is processed by a backend and the following things happen :
- The case is assigned to a nearby authority who is on patrol in that area (**Patrol App**) 
- The media in the case is processed and any known **faces detected** are added to the case info
- The case description from the citizens is proccesed to **determine the type of crime** better and is added to the case info
- The case is updated in the (**Admin Website**) in real time for higher authorities   

 
Well we talked about a lot of apps above right? let's actually see what everything does in detail down here :

1) **Patrol App** :-
- It is an app for the authorities on patrol to take up cases near them and respond as soon as possible 
- An authority can have a max of the 5 cases alloted to them ,if it exceeds that then the backend finds the next nearest patrol to allocate it to. The patrol authority can drive upto the case as we provide accurate location as well as mark the status of the case as resolved or invalidated.
- Tech Stack :- **Flutter** with BLOC State Management(Android + iOS)  
- [Github Repository](https://github.com/srikharshashi/authoritiesapp)
- [Play Store Link]()
- ScreenShots : 


2) **Intelligent part of the system** :-
- The backend houses two ML models which include an NLP model to categorize the crime based on the description as well as face detection model which detects if it's repeat offender based on perviously detected faces and if the face is unknown then it adds the face to existing facelist 
- A **crime score** is calculated based on all the data from ML model like repeat offence status,crime type and location based crime statistics for the authorities to determine how important a case is to handle it better 
- Tech Stack(Frameworks) :- **Scikit-Learn** 
- [Github Repository - Face Recognition]()
- [Github Repository - NLP]()


3) **The Admin App** :-
- The admin app is a website which provides live updates of all the cases being registered which is aimed at higher authorities to have a quick glance as well as case overview filtered by different type of parameters as required 
- It provides a central place to add patrol authorities 
- It provides location wise statistics on how the cases are distributed and how many of them are actually solved as of realtime
- [Github Repository](https://github.com/sravangvm/Sih-Admin)
- [Live URL]()
- Tech Stack :- **React JS** , **HTML** , **CSS** ,**BootStrap**
- Screen Shots :-  


###  The Backend
- The backend houses the ML Model and the crime score calculator which handles all the **REST API** requests for three apps and also enables **web socket** communication via **SocketIO** package.
- The usernames and passwords are stored as SHA256 and Argon2 hashes so that even in the event of a security breach no one is ever gonna know the actual user names of the people making it **pretty resilient to attacks** 
- As a cherry on the top if the crime is resolved the the reporter gets a certain amount of tokens trasfered to his wallet via a **smart contract** as an incentive anonymously
- Tech Stack :- **Flask** with blueprint architecture and **MongoDB** as NoSQL database and **Docker** for containerization.



### Deployment
The backend would best be deployed on an **AWS EC2** instance as it's just a docker container and the media storage/retrieval storage would be an **AWS S3** while the admin app could be deployed on **Heroku** ,the patrol and the citizens app must be deployed on repsective app stores of given platforms. 


## Architecture Diagram

![architecture diagram](https://user-images.githubusercontent.com/37980605/177811524-5eb56862-0ea7-4c6c-8d29-a30cae75da2e.jpg)


## Models 

1) Case Object 
![Mind Map](https://user-images.githubusercontent.com/37980605/177813396-fd94af69-5be0-4a02-b300-897aa2e61a8b.jpg)
---
2)User Object
![user object](https://user-images.githubusercontent.com/37980605/177813683-b99103f5-6ca1-4ef0-9d5b-9144657898af.jpg)
