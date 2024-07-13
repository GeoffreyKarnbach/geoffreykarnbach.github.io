---
layout: page
title: Spotify Language Detection
description: Effortlessly organize your Spotify playlist by song language with our own language detection model.
img: assets/img/spotify_language_detection.jpg
importance: 1
category: Data Science / Machine Learning
related_publications: false
---

#### Source code

<a href="https://github.com/GeoffreyKarnbach/SpotifyLanguageSorting">Go to the GitHub repository!</a>

#### Description
This project aims to split a the Spotify Saved Tracks Playlist into different playlists, sorted by the language of the songs.
The program can either use an own language recognition system, or a python module, called "langdetect".

#### Implementation

The code has been written in Python, using the Spotipy library, as well as pandas, numpy and matplotlib for our own language recognition.

Before the actual sorting could start, criterias had to be found to determine the language of a text, based on attributes. To do so, some experiments were made in the "language_analyse" Python Notebook, and as input data a [Kaggle Dataset](https://www.kaggle.com/datasets/basilb2s/language-detection), that has been reduced (see the Data directory for the used data).

My own language recognition is based on following attributes:
- hasFrenchSpecificWord
- hasGermanSpecificWord
- hasEnglishSpecificWord
- hasGermanSpecialChar
- hasFrenchSpecialChar
- percentageCapitalWordsAbove23 (German has much more capital words as all nouns start with a capital letter).

The attributes are sorted in their accuracy order, the most significant attributes are first in the list. As we now have the attributes, those could just be combined into a simple decision tree (unbalanced decision tree, either the attribute is true and we directly have a result, or we keep looking for the next attribute).

The accuracy of the recognition is tested with the "test_language_detection_accuracy.py" file, we have following output:

> Found a total of 2869 to test language recognition on:
<br>
> Success rate with custom decision tree: 92.85 %
<br>
> Success rate with langdetect module: 96.2 %

As the difference in the success rate is quite low (and both rates are quite high), our own implementation could realistically be used in the context of language sorting for spotify songs.

Once we have determined the language of each individual song, we can create the playlists (we therefore interact with the Spotipy API, to fetch the Saved Tracks and create playlists).

#### Run it yourself

In order to try the project out yourself, you need to replace any occurence of the strings "SPOTIPY_CLIENT_ID", "SPOTIPY_CLIENT_SECRET" and "SPOTIPY_REDIRECT_URI". Furthermore, if you want to split the language in other categories (for instance if you mainly listen to spanish and italian songs), you would need to change the supported languages from the array and either use the langdetect module (as it supports many more languages) or find your own criterias for the decision tree.

#### Further work

The project is currently not working anymore, as it was relying on a service to fetch the lyrics from any spotify song by its URI. This service unfortunately got taken down. An own implementation of such a service would be necessary to resume using the program.

Furthermore the custom language detection could greatly be improved by adding more attributes, trying out different decision trees or even using a bigger dataset and training a Machine Learning model.