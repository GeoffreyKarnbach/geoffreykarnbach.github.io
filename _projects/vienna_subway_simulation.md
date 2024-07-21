---
layout: page
title: Vienna Subway Simulation
description: Vienna Subway Simulation - Navigate Vienna's subway like a pro with our simulation, powered by the Dijkstra Algorithm for the shortest routes!
img: assets/img/vienna_subway_simulation.webp
importance: 1
category: Algorithms / Datastructures
related_publications: false
---

#### Source code

<a href="https://github.com/GeoffreyKarnbach/ViennaSubwaySimulation">Go to the GitHub repository!</a>

#### Description
This project simulates the subway network in Vienna and tries to find the fastest route between two stations by using the Dijkstra Algorithm applied on the Graph of the Vienna Subway Stations.

#### Implementation

The code has been written in Java, implementing the Dijkstra algorithm from scratch

The project can be configured by changing the value of (in the "SimConfig.java" file):
- increasedFactorForSubwayLineChange: This variable represents the overhead related to switching between two subway lines, to avoid falsely finding a shortest path, which would lead to many subway line switches (if they are not necessary to be able to reach the target destination)
- isPerformanceModeSubwayPath: Only computes the path in one direction and not both (the inverse path could sometimes be shorter, but the computational power required is doubled as the computation are done once from every direction, not suitable in a high performant environment)

The actual Dijkstra algorithm is run in the "getShortestPathDijkstra" method.

#### Run it yourself

To try out the program yourself and take a look at it, go to the "SimRunner.java" file and edit the two stations you want to find a path between.

The computed path between "Karlsplatz" and "Schottenring" is:
[Karlsplatz, Stadtpark, Landstrasse, Schwedenplatz, Schottenring]

Other paths, for instance with the Subway line U2 would be possible, but it has 5 stops instead of 4, so the path using the Subway line U4 is preferred by the dijkstra algorithm.

#### Further work

The project could be greatly enhanced by adding further parameters that would need to be considered to simulate the real subway network more accurately:
- Travel distance in seconds between two stations (measured, on average for 10 travels for instance)
- Take into account that some subway lines have a higher density in Vienna
- Add realistic waiting times for each station, depending on the weekday and the hour

Through this changes, the simulation could be used not only as a Path Finding tool, but as a traval planing system as well, as it could offer a decent time estimate for a given trip between two subway stations.

Furthermore, an API could be integrated to allow for integration in other projects.
