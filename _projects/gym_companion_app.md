---
layout: page
title: Gym Companion App
description: Transform your workouts with the Gym Companion App – track, analyze, and optimize your progress seamlessly!
img: assets/img/gym_companion_app.jpg
importance: 1
category: Mobile App
related_publications: false
---

#### Source code

<a href="https://github.com/GeoffreyKarnbach/GymCompanionApp">Go to the GitHub repository!</a>

#### Concept

As a regular Gym Goer myself, I used to rely on tracking my exercises in each gym session on a piece of paper, and later on my notes app on my phone. I always missed one aspect when tracking my progress: I could only see my current weight for each exercise, but no progression over time.

The Gym Companion App has as main goal to create gym sessions with a list of exercises, and for each exercise to be able to track one's own progress.

The Mobile App has been coded with Swift, SwiftUI as framework, and SwiftData for persisting data locally on the device, and the entire User Interface is in German.

#### Features of the App

When using the App, the user can:

- Create a new gym session ("Trainingsplan")
- Add exercises to a gym session, either pre-added exercises (all the exercise catalog from the "FitInn" gyms) or a custom exercise
- Add a custom exercise to the exercise catalog (and modify/delete them)
- See a recap for each exercise, of all the exercise executions, as well as a progress chart (line chart)
- Start a gym session (choose from the list of existing ones) and fill out for each exercise in the session today's performance (rep count, weight, execution score, exhaustion score)
- See a recap of any gym session in the past, with a list of all exercise, and their associated weights and reps

#### Possible expansions

The App has been created as a solution to a concrete problem. However, to be viable as a standalone product, further features could be added, amongst them:

- Analysis of the user's performance over time, by taking into account the weight evolution, the execution and exhaustion score
- Recommend changes upon the results of the analysis (for instance increase the weight on an exercise, replace an exercise)
- Add a cooperative mode between users, such as a leaderboard (concept known as gamification, people often enjoy competing against each other)
- Add a streak reminder (notification to remind going to the gym)
- Add the ability to share the recap screen of a gym session through social media (WhatsApp, Instagram, Snapchat...)
- Make gym session plans shareable between users to ease the use of the application together with friends when working out together

#### App screenshots
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/StartScreen.png)
<br>
Start Screen - Overview of available session plans
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/TraningsPlanDetail.png)
<br>
Detailed view of a specific session plan
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/TrainingsPlanExerciseAdd.png)
<br>
Add an exercise to a given session plan (with set count, rep count, weight)
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/TrainingsPlanExerciseList.png)
<br>
Detailed view of all exercises within a given session plan
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/TrainingsPlanExerciseEdit.png)
<br>
Reorder and remove exercises from a given session plan
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/CustomExerciseCreation.png)
<br>
Add a custom exercise to the exercise catalog
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/ExerciseList.png)
<br>
Overview list of all available exercises in the catalog
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/ExerciseDetailScreen.png)
<br>
Detail view for a specific exercise, containing a list of all sessions plans including it, a progress chart and a list of all previous exercise executions
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/ActiveTrainingsPlan.png)
<br>
Active gym session started, with a list of all planned exercises
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/ActiveExercise.png)
<br>
Active exercise view, with a list of all sets, and the ability to change the performance for each set, as well as the ability to rate today's exercise performance and exhaustion related to it
<br>

![Alt text](../../assets/img/gym_companion_app_preview_images/TrainingsPlanRecap.png)
<br>
Recap of the gym session, with a list of all exercises, with their rep count, weight and set count.
<br>