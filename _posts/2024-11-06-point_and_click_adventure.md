---
layout: post
title: "Creating a Point&Click adventure"
date:   2024-11-06 20:54:37 +0100
categories: gamedev raylib-go golang]
---

### Hackathon experience 🎉

Recently, I had the fantastic opportunity to join our company’s annual event, Kenya, a hackathon where all the engineers come together, collaborate, and dive into creative projects. This year, I was lucky enough to work on something that truly took me back to my roots in programming: collaborate designing a game engine in **Raylib Go** and creating a game based on our daily life in the office.

The [engine](https://github.com/apoloval/pctk) we created is suited for point-and-click adventure games, and it has some SCUMM-inspired mechanics to capture that classic feel.

I contributed to designing the walkbox system for room navigation, providing actors with efficient movement in designated areas. This system, inspired by SCUMM's approach, structures each room's walkable space into convex polygonal zones called “walkboxes,” enabling smooth and controlled actor movement.

Each actor is assigned a “current walkbox” based on its position in the room. When the player clicks to move an actor, the engine identifies the target walkbox based on the click location. If the actor is already in the target walkbox, they simply walk to the specified point. However, if the target is in a different walkbox, our precomputed “itinerary matrix” calculates the shortest path across the walkboxes. This matrix acts as an `𝑛×𝑛` grid where each entry points to the next walkbox in the path, facilitating efficient pathfinding without the complexity of A* algorithms.

We also integrated a debug mode to visualize walkboxes and paths, aiding in the development and troubleshooting of navigation logic. In debug mode, each walkbox is outlined, and the path taken by the actor from start to destination is visually represented. This feature allows us to confirm correct path computation and walkbox adjacency, helping optimize the room’s walkbox layout and verify expected movement.

<div style="text-align: center;">
    <img src="/asssets/images/walkbox.png" alt="walkbox system">
</div>
<br/>

Additionally, our system supports dynamic walkbox control, enabling us to enable or disable specific walkboxes to reflect changes within the room (e.g., closed doors or temporary obstacles). This flexibility enriches gameplay by introducing context-aware movement. Currently, the walkboxes are restricted to convex polygons, as this avoids the need for additional pathfinding within each box. However, we are exploring support for concave polygons, which would require actors to navigate around internal edges, adding further complexity to the pathfinding process.


### Here’s a Sneak Peek at the Result 🎥

Check out the trailer for our project below:

<div style="text-align: center;">
  <a href="https://www.youtube.com/watch?v=-ZoMIzeToEU" target="_blank">
    <img src="https://img.youtube.com/vi/-ZoMIzeToEU/0.jpg" alt="Cabify's adventure">
  </a>
</div>
<br/>

### Rediscovering My Love for Game Development 🎮

The funny thing is almost 12 years ago, I completed a course as a video game development expert, diving deep into **Ogre** and **C++** to create a 3D mini-golf game. Here’s a trailer of that earlier project:

<div style="text-align: center;">
  <a href="https://www.youtube.com/watch?v=WGmb2GUBxSc" target="_blank">
    <img src="https://img.youtube.com/vi/WGmb2GUBxSc/0.jpg" alt="4 Seasons Minigolf">
  </a>
</div>
<br/>

Coming back to game development after all these years was like reconnecting with that spark that got me into programming as a kid. This hackathon reminded me of the pure joy of creating something interactive and visual from scratch, and it left me wanting more!

There are still plenty of exciting ideas left to implement to bring this project to its full potential. Here’s a look at some of the key features we’re aiming to add:

- **Object Border Debugging**: Enhancing visual clarity for object boundaries during testing.
- **Scaling Adjustments**: Investigating solutions to improve current scaling issues.
- **Game State & Save Functionality**: Implementing save/load options to preserve player progress.
- **Configuration Support**: Adding settings for music, language, and other options for a personalized experience.
- **Image-Based Inventory**: Creating a more immersive inventory interface with images.
- **Custom Actor Animations**: Enabling animations not tied to specific actions for greater flexibility.
- So on...

