---
layout: essay
type: essay
title: "Finding a solution by using a solution!"
# All dates must be YYYY-MM-DD format!
date: 2024-04-25
published: true
labels:
  - Engineering
  - Design Patterns
---

*"If I had an hour to solve a problem I'd spend 55 minutes thinking about the problem and 5 minutes thinking about solutions."*– Albert Einstein

Design Patterns have two main usages in software development.

Common platform for developers
Design patterns provide a standard terminology and are specific to particular scenario. For example, a singleton design pattern signifies use of single object so all developers familiar with single design pattern will make use of single object and they can tell each other that program is following a singleton pattern.

Best Practices
Design patterns have been evolved over a long period of time and they provide best solutions to certain problems faced during software development. Learning these patterns helps unexperienced developers to learn software design in an easy and faster way.

## There are different design patterns?

Well yes, there are different patterns! Besides a singleton design pattern here's a few other design patterns used:

### Observer Pattern

The Observer Pattern is particularly useful in web development environments that are highly interactive and data-driven. In one of my software engineering projects, I used an application called Meteor combined with React which implements several patterns including. This pattern is used in Meteor's reactivity system. The observer pattern allows data changes on the server to be automatically pushed to the clients. Components or templates that depend on this data automatically update when the data changes. Some examples of this are 'Trackers' and 'reactive' data sources such as [Mongo.Cursor](https://docs.meteor.com/api/collections.html#Mongo-Cursor), to automatically update the UI whenever the underlying data changes.

Here is an example to set up the Meteor server to manage the state of a conference, similar to the Conference class in Javas, which will notify clients (React components) whenever there are updates:

```js
// server/publications.js
import { Meteor } from 'meteor/meteor';
import { Mongo } from 'meteor/mongo';

export const Conferences = new Mongo.Collection('conferences');

Meteor.publish('conferenceData', function publishConference() {
  return Conferences.find();
});

Meteor.methods({
  'conference.update'(details) {
    const { totalAttendees, totalSpeakers, nameEvent } = details;
    Conferences.update({}, {
      $set: { totalAttendees, totalSpeakers, nameEvent }
    }, { upsert: true });
  }
});
```

Next, create a React component that listens to changes in the conference details stored in the Meteor's database. This component will re-render whenever the conference data changes:

```js
// client/Conference.js
import React, { useState, useEffect } from 'react';
import { withTracker } from 'meteor/react-meteor-data';
import { Conferences } from '/imports/api/conferences';

function Conference({ conference }) {
  if (!conference) return <div>Loading...</div>;

  return (
    <div>
      <h1>{conference.nameEvent}</h1>
      <p>Total Attendees: {conference.totalAttendees}</p>
      <p>Total Speakers: {conference.totalSpeakers}</p>
    </div>
  );
}

export default withTracker(() => {
  Meteor.subscribe('conferenceData');
  return {
    conference: Conferences.findOne(),
  };
})(Conference);
```

* Server-Side Publication: The server publishes the details of the conference. Whenever the details are updated via the conference.update method, all subscribed clients are automatically notified due to Meteor's reactive data sources.
* React Component (Observer): The Conference React component subscribes to the conference data. This component automatically receives updates whenever the conference details change (because of Meteor's built-in reactivity with MongoDB). The withTracker HOC (higher-order component) in Meteor re-runs whenever the data changes, ensuring the React component re-renders with the updated data.

This approach has helped me replicate the observer pattern in a real-time web application setting,  and it manages data reactivity with React for the UI updates.

### Publish-Subscribe Pattern

Another pattern implemented in meteor is Publish-Subsribe pattern. Meteor uses the publish-subscribe pattern to handle data updates between the server and the client allowing clients to subscribe to data publications defined on the server, and receive updates when the data changes. 

The current pattern has also been useful for my [Manoa Reclaim](https://manoa-reclaim.github.io/), a lost an found web application. User of the website need to see updates immediately as items are reported lost or found.

On the server side, I define what data should be available to the clients. For a lost and found website, there might have collections for lost items and found items and this is how a publication would be set up:

```js
import { Meteor } from 'meteor/meteor';
import { Mongo } from 'meteor/mongo';

export const LostItems = new Mongo.Collection('lostItems');
export const FoundItems = new Mongo.Collection('foundItems');

Meteor.publish('lostItems', function() {
  return LostItems.find({ resolved: false });
});

Meteor.publish('foundItems', function() {
  return FoundItems.find({ resolved: false });
});
```
In this example, LostItems and FoundItems are MongoDB collections stored on the server. The publish functions are set up to only send items to the client that have not yet been resolved (resolved: false), meaning the item is still lost or found and not yet returned to the owner.

On the client side, you subscribe to these publications to get real-time updates. Here's how you could set up subscriptions using Meteor’s reactive context to automatically update the UI when the data changes:

```js
import { Meteor } from 'meteor/meteor';
import { withTracker } from 'meteor/react-meteor-data';
import React from 'react';

import { LostItems, FoundItems } from '/imports/api/items';

const LostAndFoundApp = ({ lostItems, foundItems }) => (
  <div>
    <h1>Lost Items</h1>
    <ul>
      {lostItems.map(item => <li key={item._id}>{item.description} - {item.location}</li>)}
    </h1>
    <h1>Found Items</h1>
    <ul>
      {foundItems.map(item => <li key={item._id}>{item.description} - {item.location}</li>)}
    </ul>
  </div>
);

export default withTracker(() => {
  Meteor.subscribe('lostItems');
  Meteor.subscribe('foundItems');

  return {
    lostItems: LostItems.find().fetch(),
    foundItems: FoundItems.find().fetch(),
  };
})(LostAndFoundApp);
```
As soon as a new lost or found item is added to the database or an item’s resolved status changes, the client UI updates automatically to reflect the change. Setting up this pattern also helps further development of the website where the state must be synced across clients instantly if there is an update to the

## The Gangs of Four

In the world of software engineering, four pioneers came together to write a book that would fundamentally change the approach to object-oriented design. Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides, collectively known as the Gang of Four, authored a seminal work that introduced a systematic catalog of design patterns. Their contributions provided a shared language and a set of best practices that have been adopted by developers worldwide. 

<img src="../img/GoF.png" alt="Alt text" width="200" height="200">

There are many different design patterns in the book and in my project I've utilized quite a few such as the Observer pattern and Publish-subscribe pattern. 

At the time of writing this essay, I am still working on a web application project. What I would like to implement in an item registration form (for lost items) is for the user to log the location they discovered the item via Google Maps. If I were to implement a feature in my application where clients can specify the location of their lost items using Google Maps, I would utilize the Facade Pattern from the Gang of Four design patterns.

This pattern would provide a simplified interface to the more complex Google Maps API subsystem. By adopting this approach, it would create a straightforward interface for users to interact with, which internally handles more complex interactions with the Google Maps API. For example, I could design a facade that allows users to simply select a location on a map, while I take care of creating markers, fetching coordinates, and translating these into a meaningful address or location description:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Google Maps Example</title>
    <style>
        /* Set the size of the map container */
        #map {
            height: 400px;
            width: 100%;
        }
    </style>
</head>
<body>
    <!-- Map container -->
    <div id="map"></div>

    <!-- Load the Google Maps JavaScript API -->
    <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap"
            async defer></script>

    <!-- Initialize the map -->
    <script>
        // Initialize the map
        function initMap() {
            var map = new google.maps.Map(document.getElementById('map'), {
                center: {lat: -34.397, lng: 150.644},
                zoom: 8
            });

            // Add a click event listener to the map
            google.maps.event.addListener(map, 'click', function(event) {
                // Get the coordinates of the click event
                var clickedLocation = event.latLng;
                var latitude = clickedLocation.lat();
                var longitude = clickedLocation.lng();

                // Display the coordinates in an alert dialog
                alert("Latitude: " + latitude + "\nLongitude: " + longitude);
            });
        }
    </script>
</body>
</html>
```

Above is an html code block of how the Google Map api would be set up in the source code. Overall, the Facade pattern here simplifies the interaction with a layer of a subsystem, allowing end-users or other developers to utilize geographical functionalities without needing to delve into the complexities of the API.

## Which design patterns will help me?

Well, it all depends on what you're desigining, whether it'd be a web application, game developing and more. However, a good guide is the GoF to help streamline both the back and front-end functionalities and make the system more efficient and user-friendly. The GoF design patterns are like blueprints that provide developers with guidelines to solve recurring problems. 
